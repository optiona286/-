# 期貨盯盤管家

台指期 TX 歷史成交資料監控與回測播放工具。專案目前是前端單頁 PWA，可用瀏覽器直接操作，支援資料夾選取、單日解析、早晚盤切分、監控事件與回測播放。

## 功能

- 選擇含每日 zip 的資料夾後建立交易日清單。
- 點選某一日才解析該日 `.rpt`，避免一次載入所有資料。
- 只讀取 `TX` 商品。
- 自動挑選單一月份契約中成交量最大者。
- 排除價差契約，例如 `202603/202604`。
- 早盤：`08:45-13:45`。
- 晚盤：`15:00-05:00`。
- 每個盤別以第一筆成交價作為參考價。
- 線圖以每分鐘為單位聚合。
- 參考價上方紅色、下方綠色，並顯示漸層區域。
- 回測可播放、暫停、前進、快進與調整秒數。
- 回測控制列可收合。
- 事件觸發時播放上漲 / 下跌音效。
- 漲跌超過 100 點時播放重大波動音效與語音提醒。
- PWA 支援，可透過 localhost 或 HTTPS 安裝。

## 專案結構

```text
.
├── index.html
├── manifest.webmanifest
├── sw.js
├── offline.html
├── server.js
├── assets/
│   ├── icon.svg
│   └── README.md
└── 期貨盯盤管家_理解紀錄.md
```

## 本機啟動

PWA 不能在 `file://` 下完整啟用 service worker，請用本機 HTTP server。

```bash
node server.js
```

開啟：

```text
http://127.0.0.1:4173/
```

## Google TTS 音檔

若要使用固定的 Google Text-to-Speech 女聲，請把音檔放在：

```text
assets/google-tts-major-up.mp3
assets/google-tts-major-down.mp3
```

沒有放音檔時，程式會退回瀏覽器內建中文語音。

## 不建議提交的資料

以下內容不適合放進 GitHub：

- `2026/` 交易資料資料夾
- 原始截圖參考圖
- 大型 zip / rpt 資料檔
- API Key 或任何金鑰

