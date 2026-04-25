# Murmuration

**A development methodology for human-agent collective intelligence**

*Version 0.1 — Working Draft*

---

## 開場

軟體開發在過去三十年經歷了三次方法論躍進:

- **Waterfall**(1970s)解決了「混亂沒有流程」的時代
- **Agile / Scrum**(2000s)解決了「需求模糊、迭代太慢」的時代
- **DevOps**(2010s)解決了「開發與運營脫節」的時代

每一次躍進的觸發點都是相同的結構:**舊瓶頸被技術消解,新瓶頸浮現,需要新方法論承接**。

我們正站在第四次躍進的門檻。

當 AI agent 進入軟體開發,**寫程式的成本快速趨近於零**。但同時,一個新的瓶頸浮出水面:**意圖在多個智能體之間的對齊成本急速上升**。

人類團隊靠默契、靠站會、靠喝咖啡時的補充對話。Agent 沒有默契。每個 agent 只能讀取它被給予的文字,而不同 agent 對同一份 spec 會產生不同的理解。每個 operator(agent 的人類主人)在事後發現分歧,只能事後修補,且常常修不完。

Scrum 解決不了這個問題,因為 Scrum 的整個架構假設「執行者是會自動同步的人類」。雙菱形設計解決不了這個問題,因為它假設「整個發散收斂過程都由人類設計師完成」。Waterfall 更不用說。

**Murmuration 是為這個新瓶頸設計的方法論。**

它的名字來自椋鳥群飛(starling murmuration)— 成千上萬隻鳥在天空中以驚人的同步性轉向、聚散、重組,卻沒有中央指揮。每隻鳥只感知它身邊七隻鄰居的動向,但整個群體展現出超越任何個體的協調與美感。

這就是 Murmuration 對未來軟體開發的願景:**人類與多個智能體共同構成一個協作群體,沒有中央 boss,但極度同步;每個成員都有獨立判斷,整體湧現出超越個體的產品**。

這個未來尚未存在。Murmuration 是召喚它的方法論。

---

## 1. Manifesto

我們在實踐中發現了更好的、人類與智能體協作開發軟體的方式。透過這個過程,我們重視:

- **意圖的清晰** 勝於 **任務的明確**
- **理解的對齊** 勝於 **文件的完備**
- **現實的驗證** 勝於 **計劃的執行**
- **漂移的偵測** 勝於 **進度的報告**
- **可能未來的探索** 勝於 **當下需求的滿足**

也就是說,雖然右項仍有其價值,我們更重視左項。

---

## 2. 五個核心原則

### 2.1 Intent over Tasks（意圖先於任務）

不規劃任務,規劃意圖。任務是執行者（人或 agent）從意圖中推導出來的。同一個 intent,不同 agent 產生的任務序列可以不同——這是特性,不是 bug。

意圖必須包含:**為什麼**（why）、**期望的世界狀態**（what）、**邊界與約束**（constraints）、**驗證機制**（verifiers）、**已知的不確定性**（open questions）。

### 2.2 Comprehension over Documentation（理解先於文件）

不追求「完美的 spec」,追求「所有執行者對 spec 的理解可被觀察、可被 diff」。

文件是死的,理解是活的。每個執行者（人或 agent）在開工前必須產出 Comprehension Snapshot,用自己的話複述意圖、列出假設、聲明計畫。系統自動 diff 這些 snapshot,分歧自動標紅、要求對齊。

### 2.3 Verifier over Acceptance Criteria（驗證先於驗收條件）

驗收條件是人類讀的,verifier 是機器（或人）可執行的。每個 intent 必須附帶可執行的 verifier,這些 verifier 同時餵給 eval 系統使用。

Verifier 是 spec 的可執行版本——是 intent 是否實現的真理判官。

### 2.4 Drift Detection over Status Reporting（漂移偵測先於進度報告）

不問「進度到哪了」,而是持續監測「執行中的理解是否偏離原 intent」。狀態報告是滯後指標,drift signal 是領先指標。

當執行的方向開始與意圖偏離,系統發出 drift signal——而不是等到 PR review 才發現。

### 2.5 Replayable Context over Tribal Knowledge（可回放脈絡先於部落知識）

所有決定背後的 context 必須可被回放。不依賴「某個 PM 記得當初為什麼這樣決定」。

Agent 沒有部落記憶,人類也不該依賴。每個重要決定都應留下 Decision Trace——基於什麼 context、考慮了什麼選項、為什麼選這個。

---

## 3. 三菱形架構（Triple Diamond）

Murmuration 不取代既有方法論,而是縫合它們,並補上多智能體時代缺失的環節。

```
[第零菱形:未來探索]  →  [第一菱形:問題定義]  →  [第二菱形:解法執行]
   Speculate / Frame      Discover / Define        Develop / Deliver
   (推測設計)             (傳統 UX 雙菱形)         (敏捷 + 多智能體對齊)
```

### 3.1 第零菱形:未來探索

繼承自 **推測設計（Speculative Design）**,Dunne & Raby 的方法論傳統。

**發散階段**:刻意引入跨領域信號（技術趨勢、社會變遷、生態壓力、跨產業類比、藝術視角、批判視角）。使用設計虛構（design fiction）、未來情境寫作、PPPP 分析（Probable / Plausible / Possible / Preferable）、反烏托邦演練（dark future drill）。

**收斂階段**:產出 **Future Frames** —— 一組組織選擇相信的「可能未來假設」。每個 frame 包含:支撐信號、時間視野、PPPP 分類、蘊含地圖、反框架（counter-frame）。

**為什麼需要這個菱形**:傳統 UX 與敏捷都假設答案藏在「現在的使用者」身上。但 AI-native 產品在創造尚未存在的行為模式,**沒有現成使用者可以訪談**。我們必須從可能的未來反推現在該做什麼。

### 3.2 第一菱形:問題定義

繼承自 **設計思維 / 雙菱形設計**（Design Council 的 Double Diamond）。

**發散階段**:在 Future Frames 的約束下進行使用者研究、田野調查、How Might We 工作坊、affinity mapping、訪談洞察萃取。

**收斂階段**:產出 **Intent Candidates** —— 候選意圖,還未進入執行,但已有完整的 why / what / constraints。

**Murmuration 對這個菱形的貢獻**:不重新發明 UX 工具,而是要求每個 Intent Candidate 必須宣告「我服務於哪個 Future Frame」。如果一個候選意圖服務不了任何 frame,就明確標註它是「當下優化」而非「未來投資」。

### 3.3 第二菱形:解法執行

繼承自 **敏捷 / Scrum**,但根本性改造以支持多智能體協作。

**發散階段**:Ready Intent 被分派給多個執行者（人 + agent 混合）。每個執行者產出 Comprehension Snapshot——對意圖的獨立理解、假設、計畫。

**收斂階段**:系統自動 diff 多份 snapshot,將分歧顯性化。團隊在 Comprehension Sync 中對齊收斂。對齊後執行,持續監測 Drift Signal,verifier 持續驗證。

**Murmuration 對這個菱形的貢獻**:這是傳統敏捷沒處理的——當「發散」階段是多個 agent 而非多個人類時,默契式的對齊不再可行。Comprehension Snapshot 是 Murmuration 真正獨特的核心物件。

---

## 4. 核心物件

Murmuration 定義一組標準物件,作為人類與 agent 共同處理的協作單位。每個物件都按 protocol 級別的精確度設計,即使目前作為方法論使用,也保留未來升級為 protocol 的可能。

### 4.1 Future Frame

組織當前選擇相信的某個未來假設。

**核心欄位**:
- `id`: 唯一識別碼
- `name`: 人類可讀的名稱（例如:「2028 年每個專業使用者擁有 5+ 個個人 agent」）
- `signal_set`: 支撐這個 frame 的證據與信號
- `time_horizon`: 時間視野（18 個月 / 3 年 / 10 年）
- `pppp_classification`: Probable / Plausible / Possible / Preferable
- `implication_map`: 如果這個 frame 為真,對使用者行為、產品形態、組織能力的蘊含
- `counter_frame_ref`: 刻意保留的反對假設
- `monitoring_signals`: 用來追蹤這個 frame 是否仍然成立的指標
- `status`: active / monitoring / retired

### 4.2 Intent

一個帶有完整 context 的意圖物件。Murmuration 的最小工作單位。

**核心欄位**:
- `id`: 唯一識別碼
- `version`: 語意版本號
- `why`: 商業目標、客戶證據引用、放棄條件
- `what`: 期望的世界狀態（不是步驟序列）
- `constraints`: 絕對不能違反的邊界
- `verifiers`: 可執行的驗證機制清單
- `open_questions`: 已知的不確定性
- `future_frame_refs`: 此意圖服務於哪些 Future Frame
- `context_bundle_ref`: 對應的脈絡包
- `parent_intents`: 父意圖（若是分解出來的子意圖）
- `state`: draft / debated / refined / ready / in_execution / verified / done / abandoned

**Intent 的人類可讀表述**（基於 Jobs Story 格式）:
> 當 [情境] 時，[使用者類型] 想要 [動機]，這樣他們就能 [預期結果]。

### 4.3 Context Bundle

可版本化的上下文包。每個執行單元拿到一個明確的 bundle,而不是「請去 Notion 找」。

**核心欄位**:
- `id`, `version`
- `documents`: 相關文件、設計、規格
- `code_references`: 相關程式碼模組
- `decision_traces`: 相關過往決定
- `related_intents`: 相關意圖
- `stakeholder_voices`: 客戶訪談、回饋摘錄

Bundle 是一級公民,可被引用、diff、繼承。

### 4.4 Comprehension Snapshot

執行者（人或 agent）在開工前對意圖的獨立理解快照。

**核心欄位**:
- `id`, `intent_ref`, `executor`（人類或 agent 的識別）
- `timestamp`, `signature`（避免事後篡改）
- `restated_goal`: 用自己的話複述意圖
- `assumptions`: 我打算做出的假設清單
- `plan`: 我計畫的執行路徑（粗略,非詳細任務）
- `edge_cases`: 我認為需要特別處理的邊界情況
- `tools_intended`: 我打算使用的工具與資源
- `concerns`: 我看到的風險或不確定性

這份 snapshot **必須在開工前產出,且必須與其他執行者的 snapshot 比對**。多份 snapshot 之間的分歧由 Comprehension Sync 處理。

### 4.5 Decision Trace

每個重要決定（無論人或 agent 做的）留下軌跡。

**核心欄位**:
- `id`, `intent_ref`, `decided_by`, `timestamp`
- `context_at_decision`: 決定當下看到的脈絡
- `options_considered`: 考慮過的選項
- `chosen_option`: 選了哪個
- `rationale`: 為什麼這樣選
- `reversibility`: 是否可逆,若不可逆則特別標註

這不是事後文件,是工作流原生產物。

### 4.6 Drift Signal

當執行中的理解開始偏離原 intent,系統發出的訊號。

**核心欄位**:
- `id`, `intent_ref`, `detected_at`
- `drift_type`: scope_creep / assumption_violation / verifier_failure / context_change / other
- `evidence`: 觸發此訊號的具體證據
- `severity`: low / medium / high / critical
- `suggested_action`: continue / sync / renegotiate / abandon

Drift Signal 是領先指標——讓問題在事後 review 之前就被發現。

### 4.7 Verifier

可執行的驗證機制,確認意圖是否實現。

**Verifier 類型**:
- **Code-based**: 自動化測試、eval 套件、效能基準
- **Prompt-based**: 用 LLM 評估的結構化判斷
- **Human-in-the-loop**: 人工檢核流程
- **Composite**: 多個 verifier 的組合

每個 verifier 有明確的介面:給定一個世界狀態,回傳通過 / 失敗 / 不確定。

---

## 5. 角色

Murmuration 不取消既有角色（PM、設計、工程、QA）,但新增三個概念性角色,每個人類成員可身兼多角:

### 5.1 Intent Author

意圖的書寫者與守護者。負責將 Future Frame 與使用者洞察熔煉成 Ready Intent。對 Intent 的清晰度、verifier 設計、context bundle 完整性負責。

通常由 PM 或 Product Strategist 擔任。

### 5.2 Operator

人類 agent 主人。負責:
- 管理一個或多個 agent 的執行
- 確保自己的 agent 產出的 Comprehension Snapshot 真實反映其理解
- 監測 Drift Signal 並回報
- 在 Comprehension Sync 中代表自己 agent 的觀點

每個工程師、設計師,在使用 agent 工具時,自動成為 Operator。

### 5.3 Verifier Curator

驗證機制的設計者與維護者。負責:
- 為每個重要 Intent 設計可執行的 verifier
- 維護組織的 eval 資料集
- 確保 verifier 隨產品演化而更新

通常由 QA、ML engineer、或產品分析師擔任。在 AI-native 產品中,這個角色的份量遠超過傳統 QA。

---

## 6. 儀式（Ceremonies）

Murmuration 定義五個核心儀式,對標 Scrum 的儀式但本質不同。

### 6.1 Future Forge（對標:無）

**目的**:更新組織的 Future Frames Set。

**節奏**:每季一次。

**參與者**:跨整個組織,刻意納入跨領域聲音（學術、其他產業、藝術家、批判視角者）。

**產出**:更新 Future Frames Set——哪些 frame 退役、哪些升級為主動投資、哪些 counter-frame 需要監控。

**為什麼存在**:Scrum 連「我們為什麼存在」都不問,預設這件事在 sprint 之外解決。Murmuration 把它顯性化。

### 6.2 Intent Forge（對標:Sprint Planning）

**目的**:將 Future Frame + 使用者洞察熔煉成 Ready Intent。

**節奏**:依需要,通常每兩週一次。

**參與者**:Intent Author 主持,設計師、技術窗口、領域專家參與。**人類限定,agent 不參與這個儀式**——因為這是發散與辯論的場域,需要保留模糊與多義的空間。

**產出**:從候選 Intent 中提升為 Ready Intent 的清單,進入第二菱形的執行。

**進入 Ready 的條件（Definition of Ready for Multi-Agent Execution）**:
- 至少兩位人類能用自己的話複述意圖
- 主要邊界案例已被列出並有處理方向
- 有明確可執行的 verifier
- Context Bundle 已組裝完成
- 已宣告服務於哪個 Future Frame

### 6.3 Comprehension Sync（對標:Daily Standup）

**目的**:對齊所有執行者（人 + agent）對當前 Intent 的理解。

**節奏**:Intent 進入執行時的第一次必開,後續視 Drift Signal 觸發。

**參與者**:該 Intent 的所有 Operator（人類）。

**產出**:基於各自 Comprehension Snapshot 的對齊結論。發現分歧時即時收斂,或回到 Intent Forge 重議。

**重點**:這個會議的核心問題不是「你做了什麼」,而是「你現在認為我們要做的是什麼、你打算怎麼做」。是**理解的同步**,不是**狀態的回報**。

### 6.4 Drift Review（對標:無）

**目的**:檢視所有 active Intent 的 Drift Signal,決定是否需要重議。

**節奏**:每週一次,輕量化。

**參與者**:Intent Author + 相關 Operator。

**產出**:對每個有 drift signal 的 intent 的決定——continue / sync / renegotiate / abandon。

**為什麼存在**:這是 Murmuration 對「敏捷」的最大改造。Sprint Review 是事後檢討,Drift Review 是事中干預。

### 6.5 Reality Check（對標:Sprint Review）

**目的**:對照 Verifier 結果,確認 Intent 是否實現。

**節奏**:Intent 完成時。

**參與者**:Intent Author、Operator、Verifier Curator、利害關係人。

**產出**:Intent 狀態轉為 verified / needs_iteration / abandoned。

### 6.6 Mesh Retro（對標:Retrospective）

**目的**:不只回顧人類團隊,也回顧 agent 的表現、context bundle 的品質、verifier 的有效性。

**節奏**:每月一次。

**參與者**:全體成員。

**產出**:對方法論本身、agent 配置、context 結構、verifier 設計的改進行動。

---

## 7. Intent 生命週期狀態機

```
                    ┌──────────┐
                    │  draft   │  ← 從 Intent Forge 發散階段產出
                    └────┬─────┘
                         │
                         ▼
                    ┌──────────┐
                    │ debated  │  ← 經過辯論與 refine
                    └────┬─────┘
                         │
                         ▼
                    ┌──────────┐
                    │ refined  │  ← 接近 ready 但 verifier 尚未設計完成
                    └────┬─────┘
                         │
                         ▼
                    ┌──────────┐
                    │  ready   │  ← 通過 Definition of Ready,可進入執行
                    └────┬─────┘
                         │ Comprehension Snapshots 產出並對齊
                         ▼
              ┌───────────────────┐
              │  in_execution     │
              └────┬──────────────┘
                   │
        ┌──────────┴──────────┐
        ▼                     ▼
   ┌──────────┐        ┌──────────────┐
   │ verified │        │drift_detected│
   └──────────┘        └──────┬───────┘
        │                     │
        ▼                     ▼
   ┌──────────┐        ┌──────────────┐
   │   done   │        │ renegotiation│ → 回到 refined / ready
   └──────────┘        └──────────────┘
                              │
                              ▼
                        ┌──────────┐
                        │abandoned │
                        └──────────┘
```

每個狀態轉移有明確的觸發條件、必要的 artifact、誰可以觸發。這個狀態機是 Murmuration 從方法論升級為 protocol 時的核心骨架。

---

## 8. 與既有方法論的關係

Murmuration 不是革命,是縫合與擴展。誠實標註它的繼承:

| 既有方法論 | Murmuration 繼承的部分 | Murmuration 改造或新增的部分 |
|---|---|---|
| **Speculative Design**（Dunne & Raby） | 第零菱形整體架構、設計虛構、PPPP、跨領域發散 | 將 Future Frame 結構化為可被 Intent 引用的物件 |
| **Double Diamond**（Design Council） | 第一菱形的整體流程、發散收斂的辯證結構 | 要求每個 Intent Candidate 連結到 Future Frame |
| **Jobs-to-be-Done** | Intent 的人類可讀層格式 | 增加 verifier、constraints、context bundle 等可執行欄位 |
| **Scrum** | 迭代節奏、retro 文化、人類團隊協作儀式 | 取消 Sprint 為唯一節拍器、新增 Drift Review、Comprehension Sync 取代 Standup |
| **XP / TDD** | 驗證先於實作的精神 | Verifier 涵蓋更廣（不只測試,包含 eval 與人類判斷） |
| **DevOps / CI-CD** | 持續驗證、快速反饋 | Drift Signal 作為新型反饋機制 |
| **Dual-Track Agile**（Marty Cagan） | Discovery 與 Delivery 分軌 | 三軌而非雙軌（加上 Speculation）,且明確處理 agent 協作 |

**Murmuration 真正獨特的貢獻**:
1. **Comprehension Snapshot 機制**——多智能體理解對齊的顯性協議
2. **Drift Signal 機制**——將「對齊偏移」作為一級可觀測指標
3. **Future Frame 與 Intent 的硬連結**——逼迫每個產品決定回答「我們相信什麼未來」

---

## 9. 與既有 Protocol 的關係

Murmuration 設計時考慮未來升級為 protocol。在這個視野下,它與既有 agent protocol 的分層關係:

- **MCP (Model Context Protocol)**:處理 agent 如何取得 context
- **A2A (Agent2Agent)**:處理 agent 如何與另一個 agent 直接通訊
- **Murmuration**:處理多個 agent + 人類**如何在共同意圖下對齊與協作**

Murmuration 不與既有 protocol 競爭,而是站在它們之上,補完它們缺的「意圖協作層」。

---

## 10. 採用路徑（Adoption Path）

Murmuration 不需要組織一次性轉型。建議的漸進採用路徑:

### Stage 1:單點實驗（0–3 個月）

- 選一個專案或產品線試行
- 用 Notion / Linear 等既有工具承載 Intent / Comprehension Snapshot 等物件
- 跑 1-2 個完整 Intent 生命週期
- 記錄痛點與意外

**成功訊號**:多 agent 任務的返工率下降、operator 之間的事後對齊會議減少。

### Stage 2:組織擴展（3–12 個月）

- 將試行經驗萃取為組織內標準
- 引入 Future Forge 儀式
- 建立組織級 Future Frames Registry
- 訓練 Verifier Curator 角色

**成功訊號**:roadmap 討論明顯往「服務於哪個 Future Frame」收斂、產品決定的可追溯性提升。

### Stage 3:Protocol 化（12 個月以後,可選）

- 將核心物件的 schema 開源
- 與其他組織建立互通實驗
- 進入產業標準對話

**成功訊號**:其他組織採用、跨組織 agent 協作成為可能。

---

## 11. 盲點與未解問題

誠實列出 Murmuration v0.1 已知的限制。這些不是失敗,是未來工作的方向。

### 11.1 意圖辯論的成本可能爆炸

如果每個小改動都要走 Intent Forge,組織會癱瘓。需要設計「輕量 intent」與「重量 intent」的分流機制,目前 v0.1 尚未明確規範。

### 11.2 Verifier 不是萬能

許多產品價值（美感、體驗、品牌調性、敘事力）很難寫成可執行 verifier。這部分仍需人類判斷。Murmuration 不應假裝能自動化所有驗證。

### 11.3 多智能體對齊的工程現實

Comprehension Snapshot 的自動 diff、Drift Signal 的自動偵測,技術上仍在早期。目前的實踐大多需要人類手動操作這些機制。

### 11.4 推測設計的菁英主義風險

推測設計被批評為由設計學院、白人、西方視角主導。Murmuration 採用時必須警覺,刻意納入多元視角,否則 Future Frames 會變成同溫層產物。

### 11.5 組織耐心問題

第零菱形的回報週期是年,季度 KPI 文化的組織很難容忍。Murmuration 需要「將長期 frame 翻譯成季度可觀測指標」的橋樑工具,目前尚未提供。

### 11.6 「方法論」與「protocol」的張力

推測設計的精神是保留多義性、鼓勵詮釋。Protocol 的本質是消除歧義、強制執行。Murmuration 同時想要兩者,這個張力如何長期維持是未解問題。

---

## 12. 召喚

Murmuration 不是答案,是邀請。

它假設一個尚未存在的協作未來——人類與多個智能體像椋鳥群飛般同步、湧現、創造。它不保證這個未來會到來,但它提供工具讓我們開始建構它。

如果你正在感受到舊方法論的瓶頸:
- 你的 PM 工具被 agent 撐裂
- 你的團隊在 spec 同步上花的時間多於寫程式
- 你的產品決定追不上模型能力的演化
- 你看見方法論需要被重新發明

那這份文件是給你的。

Murmuration v0.1 是 working draft。它應該被質疑、被批判、被改寫。它的最終形態應由實踐者社群共同決定,不是由任何單一作者欽定。

---

## 附錄 A:詞彙表

- **Murmuration**:本方法論的名稱。指椋鳥群飛現象,隱喻多智能體去中心化同步協作。
- **Intent**:本方法論的最小工作單位。帶有完整 context 的意圖物件。
- **Future Frame**:組織選擇相信的某個未來假設,由推測設計過程產出。
- **Comprehension Snapshot**:執行者在開工前對意圖的獨立理解快照。
- **Drift Signal**:執行中的理解偏離原意圖的訊號。
- **Operator**:人類 agent 主人,負責管理一個或多個 agent 的執行。
- **Verifier**:可執行的驗證機制,確認意圖是否實現。
- **Triple Diamond**:Murmuration 的三菱形架構（推測 → 定義 → 執行）。

---

## 附錄 B:版本歷史

- **v0.1**（2026）— 初始 working draft。提出三菱形架構、五原則、核心物件、儀式、與既有方法論的關係。

---

*這份文件本身遵循 Murmuration 的精神——它是一個 design fiction artifact,召喚一個尚未存在的協作未來。它應該被改寫,而不是被遵守。*
