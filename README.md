# 2026 葡萄牙・西班牙巡演 · 行前手冊

給藝姿舞集國樂團員的互動式網頁行前手冊。團員點自己的名字，就會看到依**樂器／性別**客製的行李、演出與行前須知。

🔗 **線上版：<https://sophy951.github.io/iberia-2026/>**

---

## 這個 repo 是什麼
- **`index.html` 就是整份手冊**——單一、自包含的 HTML 檔（CSS／JS 全部 inline，沒有 build、沒有相依套件，可離線開）。
- 所有內容都寫在檔案最上面的 **`DATA` 區**（純資料物件），看得懂就能改。

## 怎麼更新（遠端也能做）
1. **取得檔案**：`gh repo clone sophy951/iberia-2026`，或直接在 GitHub 網頁上編輯 `index.html`。
2. **改 `index.html` 最上面的 `DATA` 區**：
   - `VERSION` / `UPDATED`：版本與更新日期（顯示在頁尾，團員靠它確認是不是新版）
   - `MEMBERS`：團員名單＋每人樂器行李、譜架、房間
   - `PACK_TRIP` / `PACK_CATEGORIES` / `SPARES`：行李清單與依樂器的備品
   - `SETLIST` / `MAKEUP` / `COSTUME` / `NOTES`：演出與行前須知
   - `STATIONS` 等：每日行程
3. **驗證**：本機在檔案目錄跑 `python3 -m http.server 8000`，瀏覽器打開實際點看看（選名字、切分頁、展開／收合、打勾）。
4. **改完務必更新 `UPDATED` 日期**——不然頁尾版本會「假新」，團員無法判斷是不是最新。
5. **發佈**：`git add index.html && git commit -m "..." && git push` → GitHub Pages 會自動重建（約 30 秒～2 分鐘）上線。

### Pages 沒上線？
- 平常 30 秒～2 分鐘。若超過約 **10 分鐘**還卡在 `building`：
  1. 先看 <https://www.githubstatus.com/> 是不是 Pages 在出事。
  2. GitHub 正常但就是卡（單一 build 卡死）→ 戳它重建：
     ```
     gh api repos/sophy951/iberia-2026/pages/builds -X POST
     ```
     通常幾十秒就上。
- 驗證上線：把線上頁面抓下來跟本地 `index.html` 比對即可。

## 結構重點
- **3 分頁**：每日行程（時間軸）／行李／演出・須知。
- 統一「暖色標頭卡片」的視覺語言；行李各類別可各自收合，樂器／登機／託運常駐展開。
- 每人資料依所選名字即時渲染；打勾狀態存在瀏覽器 `localStorage`（各自裝置，不會互相影響）。

---

*藝姿舞集 30 週年 · 2026 西葡藝術節巡演*
