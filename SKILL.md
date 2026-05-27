---
name: meeting-minutes-organizer
description: Organize messy meeting notes, transcripts, or discussion records into concise structured meeting minutes. Use when the user asks to summarize a meeting, extract key discussion points, decisions, action items, owners, deadlines, follow-up items, or produce a standardized Chinese meeting report.
---

# Meeting Minutes Organizer

## Purpose

Turn unstructured meeting content into a clear, actionable meeting record. Preserve what was actually discussed, condense long discussion into useful points, and make decisions, owners, deadlines, and next follow-ups easy to scan.

## Core Principles

- Preserve accuracy: do not invent decisions, tasks, owners, dates, or attendees that are not present or strongly implied.
- Keep concise: summarize repetitive discussion into short points.
- Make actions executable: write each task as a concrete action.
- Assign accountability: include owners whenever named or inferable from explicit department/person responsibility.
- Record timing: capture deadlines, dates, time ranges, and follow-up timing.
- Mark unknowns clearly: use `未指定` when an owner or deadline is missing.

## Workflow

1. Identify meeting metadata: meeting name, date, attendees, and topic if provided.
2. Analyze the main meeting theme.
3. Extract the most important discussion points.
4. Separate final decisions from general discussion.
5. Build action items from assigned responsibilities, commitments, and next steps.
6. Add owners and deadlines from the source text.
7. Produce the standard output format.

## Extraction Rules

- Treat sentences with "決議", "確定", "同意", "採用", "由...負責", "預計", "需完成", or similar language as likely decisions or action items.
- When one deadline applies to multiple tasks, apply it to each related task.
- If a department is assigned responsibility, use the department as the owner.
- If a person and department are both mentioned, prefer the person unless the department is clearly the accountable owner.
- Keep action item text short, usually a verb-object phrase such as `完成包裝設計` or `洽談通路合作`.
- If meeting metadata is absent, omit it unless the user specifically asks for the full report template.

## Standard Output

Use this format by default:

```markdown
【會議摘要】

(100字內摘要)

【討論重點】

1.
2.
3.

【決議事項】

1.
2.
3.

【待辦事項】

| 項目 | 負責人 | 期限 |
|------|--------|------|
|      |        |      |

【下次追蹤】

-

【備註】

-
```

## Full Meeting Report Template

Use this longer template when the user asks for a formal meeting report, full meeting minutes, or explicitly provides meeting name/date/attendees:

```markdown
會議名稱：

會議日期：

與會人員：

------------------------------------------------

一、會議摘要

-

------------------------------------------------

二、討論重點

1.
2.
3.

------------------------------------------------

三、決議事項

1.
2.
3.

------------------------------------------------

四、待辦事項

| 項目 | 負責人 | 期限 |
|------|--------|------|
|      |        |      |

------------------------------------------------

五、下次追蹤事項

-

------------------------------------------------

六、備註

-
```

## Example

Input:

```text
今天討論新產品上市計畫，
行銷部負責廣告宣傳，
設計部負責包裝設計，
業務部負責通路洽談。

預計8月底完成準備工作。
```

Output:

```markdown
【會議摘要】

本次會議主要討論新產品上市計畫與各部門分工。

【討論重點】

1. 新產品上市時程規劃
2. 各部門工作分配
3. 8月底完成上市準備

【決議事項】

1. 行銷部負責廣告宣傳
2. 設計部負責包裝設計
3. 業務部負責通路洽談

【待辦事項】

| 項目 | 負責人 | 期限 |
|------|--------|------|
| 廣告宣傳 | 行銷部 | 8月底 |
| 包裝設計 | 設計部 | 8月底 |
| 通路洽談 | 業務部 | 8月底 |

【下次追蹤】

確認各部門執行進度。

【備註】

-
```
