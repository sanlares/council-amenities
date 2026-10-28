# Open Amenities: Product Requirements Document

| | |
|---|---|
| **Version** | 0.1 (draft for review) |
| **Date** | 28 October 2026 |
| **Status** | Draft |
| **Product stage** | Clickable prototype with sample data, moving to MVP |
| **Prototype** | https://sanlares.github.io/council-amenities/ |
| **Owner** | Product lead (to be confirmed) |

How to read this document: statements are tagged as **Fact** (sourced, see Appendix A), **Assumption** (believed true, not yet validated) or **Recommendation** (a proposal, with the reason). Requirement IDs (FR-xxx, NFR-xxx) are stable and can be used in tickets.

---

## 0. Assumptions

These assumptions shaped the whole document. Each one is revisited in Section 19.

1. **Business model is hybrid.** Phase 1 launches as an independent civic tech product built only from public information. Phase 2 sells a data publishing service to councils, who supply and verify their own data.
2. **One pilot area.** Phase 1 covers a single local government area (LGA): the City of Sydney, because the prototype already uses it and its open data hub publishes facility locations.
3. **Web only, no accounts.** Residents use a mobile-first website. No login, no native app in the MVP.
4. **Small team.** One product/design lead, one developer and one part-time data curator for Phase 1.
5. **Per-facility running costs are mostly not public.** Councils publish costs by asset class or service, not by individual facility. The MVP must work well with partial data. This is based on research (Section 2) and is the single most important assumption to test.
6. **Audience is Australian residents, in English first.** Translations come later.
7. **Phase 1 funding is limited** (self-funded or small grant). Data curation effort, not software, is the main cost.

---

## 1. Product Overview

| Item | Summary |
|---|---|
| **Name** | Open Amenities (working name) |
| **Concept** | A map of the public places a council runs (pools, libraries, parks, community centres, sports grounds, toilets). Tap a place to see, in plain English, what it cost to build, what it costs to run, who looks after it, why it is there and how the decision was made, with a source for every figure. |
| **Problem** | Council spending information exists, but it is spread across long PDFs, aggregated by asset class and written for auditors, not residents. Residents cannot answer simple questions about the places they use and pay for. |
| **Target users** | Residents and ratepayers first. Engaged locals (advocates, journalists, councillors) second. Council staff as the Phase 2 customer. |
| **Proposed solution** | Start from the place, not the spreadsheet. A fast, accessible map and list, a facility page with sourced facts, honest labels where data is missing, and a way to request missing data or report errors. |
| **Stage** | Prototype validated internally with sample data. Next step: MVP with real public data for one LGA. |

---

## 2. Problem Statement

### 2.1 The user problem

A resident walking past their local pool, reading a rate notice or following a debate about a rate rise has simple questions:

- What did this place cost, and what does it cost every year?
- Who maintains it: the council or a contractor?
- Why is it here, and who decided?
- Is it in good condition, and is any work planned?

Today the answers, when they exist, are scattered across:

| Source | What it contains | Why it does not work for residents |
|---|---|---|
| Operational Plan and budget (IP&R documents) | Service budgets and capital works lists | Hundreds of pages of PDF, organised by service or program, not by place |
| Annual financial statements, Report on Infrastructure Assets | Condition (1 to 5), required vs actual maintenance, backlog | Aggregated by asset class ("buildings", "open space"), not per facility. Backlog figures are unaudited (**Fact**) |
| Council meeting business papers and minutes | Decisions, resolutions, project costs | Hard to search, legal language, spread over years |
| Contracts register (GIPA Act, contracts of $150,000 or more) | Contractor names, contract values and terms | A table with no link to the place it relates to |
| Open data hub (ArcGIS) | Facility locations and attributes | No money, no decisions, no context |
| GIPA access applications | Anything not proactively published | Slow, formal, most residents do not know the option exists |

### 2.2 Existing alternatives

| Alternative | What it does well | Gap this product fills |
|---|---|---|
| NSW "Your Council" (OLG) and Victoria "Know Your Council" | Council-level comparisons, annual time series | No facility-level view. Victoria's framework has had data reliability issues (**Fact**, VAGO 2019) |
| Budget simulators (Delib Budget Simulator, Balancing Act) | Residents explore budget trade-offs during consultation. Used by City of Melbourne, Hume, Moreland, Livingstone (**Fact**) | Campaign tools for a consultation window. Not a permanent reference about specific places |
| US transparency portals (ClearGov, OpenGov) | Finance dashboards and budget books for councils | Finance-centric, built around the chart of accounts, US market |
| Engagement platforms (Granicus EngagementHQ, Open Point, Engagement Hub) | Consultation projects, surveys, map comments | Project-based, not a standing record of facility costs |
| Snap Send Solve and council request forms | Reporting a broken item | Reporting only. No cost or decision information |
| Council website facility pages | Opening hours, bookings | Never show cost, maintainer or decision history |

### 2.3 Pain points

- **Residents:** the information is technically public but practically invisible. Numbers have no context ("$1.9 million" means little without "per resident" or "per visit").
- **Engaged locals:** checking a claim in a rate rise debate takes hours of PDF reading.
- **Councils:** they publish a lot but still get the same questions, informal requests and GIPA applications. Trust does not rise with volume of documents.

### 2.4 Why it matters

- **Fact:** Australia has 537 councils spending about A$48 billion a year (2023-24, ALGA).
- **Fact:** ALGA's 2026 National State of the Assets report puts renewal and upgrade demand at up to $280 billion, with about 9% of council assets in poor condition. Residents will be asked to fund this.
- **Fact:** Rate rise disputes are ongoing. IPART assessed special variation applications from 10 NSW councils for 2026-27. In 2025, more than 90% of survey respondents opposed North Sydney's proposed increase, and IPART has noted ratepayer concerns about how councils consult.
- **Fact:** The APSC's 2025 trust report found that trust in local government is driven more by openness than trust in other levels of government.
- **Fact:** In NSW, councils must publish IP&R documents and a contracts register. In Victoria, councils must adopt a public transparency policy (Local Government Act 2020, s57). The obligation to be open exists. The usable format does not.

### 2.5 Evidence vs assumptions

| Type | Statement |
|---|---|
| Fact | Facility-level cost data is rarely published proactively. Published cost data is aggregated by asset class or service. |
| Fact | Around 1 in 5 Australian adults have low literacy or numeracy (PIAAC 2011-12, the latest Australian data). |
| Assumption | Residents care enough about specific facilities to visit a site about them when triggered (rate notice, closure, local news, consultation). |
| Assumption | Councils will see value in a resident-friendly publishing layer and pay for it once residents use the independent version. |
| Assumption | Making gaps visible ("Not published by council") creates useful pressure to publish, rather than hostility. |

---

## 3. Goals

1. **Fast answers.** A resident in the pilot area can find a facility and understand what it costs and who looks after it in under 60 seconds on a phone, without opening a PDF.
2. **Everything traceable.** Every figure and claim can be traced to a public source in one tap. No unsourced numbers.
3. **Honest about gaps.** Missing information is clearly labelled and residents can request it in under two minutes.
4. **Proof of demand.** Show that residents use the product when triggered, measured by residents reaching a facility's cost information (target in Section 14).
5. **A council partner.** At least one council signs a paid pilot or letter of intent within 9 months of launch.
6. **Usable by everyone.** Meets WCAG 2.2 AA and is understandable by people with low numeracy.

---

## 4. Non-Goals

The MVP will not:

- Show the whole council budget or every line of spending. Only facilities residents can visit.
- Compare councils with each other. NSW "Your Council" and "Know Your Council" already do this.
- Run budget simulations or participatory budgeting.
- Take maintenance or issue reports. It links to the council's existing channel or Snap Send Solve instead.
- Host comments, forums or ratings of facilities. Moderation cost and political risk are too high for a small team.
- Estimate or model costs the council has not published.
- Cover more than one LGA.
- Offer accounts, notifications, native apps or translations.
- Cover roads, footpaths, drainage and other network assets. They are not "places" a resident can choose on a map.

---

## 5. Target Users

| Persona | Context | Main problem | Motivation | Constraints |
|---|---|---|---|---|
| **P1. Everyday resident** (primary) | On a phone, triggered by a rate notice, a closed pool, a news story or a neighbour's post | Cannot find simple facts about places they use | Curiosity, fairness, "is my money well spent?" | Low time, low patience for jargon, may have low numeracy, may use assistive technology |
| **P2. Engaged local** (residents' group, precinct committee member, local journalist, councillor) | Laptop or phone, during a debate or consultation | Checking claims takes hours across PDFs | Wants credible, citable facts to share | Needs sources, links to share, ability to quote |
| **P3. Council staff** (communications, engagement, asset or finance team; Phase 2 customer) | At work, preparing consultations, answering enquiries | Publishes a lot, still fields repeat questions and GIPA requests; low trust | Fewer repeat enquiries, better consultation outcomes, meet transparency obligations | Limited time, data spread across asset, finance and records systems, cautious about publishing |
| **P4. Data curator** (internal role, Phase 1) | Desktop, weekly | Turns public documents into structured, sourced data | Accurate, current data with little rework | Part-time, needs validation to catch mistakes |

---

## 6. User Stories

Ordered by MVP importance.

1. As a **resident**, I want to see the council places near me on a map, so that I can find the one I care about.
2. As a **resident**, I want to see what a place costs to run each year and what it cost to build, so that I understand where my rates go.
3. As a **resident**, I want those numbers put in everyday terms (per resident, per visit), so that I can judge whether they are big or small.
4. As a **resident**, I want to know who looks after a place (council team or contractor), so that I know who is responsible.
5. As a **resident**, I want to know why a place is where it is and how the decision was made, so that I can understand the reasoning.
6. As an **engaged local**, I want to see the source of every figure, so that I can trust and quote it.
7. As a **resident**, I want to know clearly when the council has not published something, so that I am not misled by an empty or invented number.
8. As a **resident using a screen reader or keyboard**, I want a list that does everything the map does, so that I am not excluded.
9. As a **resident**, I want to share a link to a specific place, so that I can make a point in a group chat or community page.
10. As a **resident**, I want to request missing information from the council easily, so that gaps get filled.
11. As an **engaged local**, I want to report an error, so that the data stays accurate.
12. As a **resident**, I want to see planned works and condition, so that I know whether a problem is being dealt with.
13. As a **data curator**, I want validation that blocks publishing bad or unsourced data, so that mistakes do not go live.
14. As **council staff** (Phase 2), I want to upload our own data and mark it verified, so that residents see official figures and we answer fewer repeat questions.

---

## 7. User Journey / Core Flows

### Flow 1. Find a place and understand its cost (primary)

1. Resident opens the site (direct, search engine or shared link).
2. Sees the map and a list of places in the LGA, with category filters and a summary ("These 64 places cost $X a year to run, where published").
3. Taps a marker or list item.
4. Facility page opens (side panel on desktop, bottom sheet on mobile) with name, type, address and key facts.
5. Reads "The money": build cost, yearly running cost, per resident and per visit, each with its financial year and a source link.
6. Optionally reads "Why it is here", "How it was decided", "Who looks after it", "History and planned works".
7. Shares the link, gets directions, or goes back to the list.

Alternative paths and edge cases:
- **No cost published:** the money section shows "Not published by the council" with a short explanation and a "Request this information" button (Flow 4). It also shows the service-level figure if available ("The council spends $X a year on all its pools").
- **Facility closed or under construction:** status banner at the top of the page; costs still shown.
- **Map fails to load:** list view remains fully usable; a notice explains the map is unavailable.

### Flow 2. Find a place without the map

1. Keyboard or screen reader user lands on the page; a skip link goes to the list.
2. Searches by name, suburb or type, or filters by category.
3. Results announce their count; each item reads name, type, suburb, age and yearly cost.
4. Opens the facility page; focus moves to the page heading. Escape or "All places" returns focus to the same list item.

### Flow 3. Arrive from a shared link

1. Resident opens a link to a specific place.
2. Facility page renders directly (with the map centred on it), with a clear way back to all places.
3. If the place no longer exists or the link is wrong, a "Place not found" page offers search and the full list.

### Flow 4. Request missing information

1. On a field marked "Not published", resident taps "Request this information".
2. A panel explains the two options in plain words: ask the council informally (email or web form) or make a formal access application (GIPA in NSW).
3. A pre-written request is shown, naming the facility and the specific information. Resident can copy it or open the council's form.
4. Resident optionally confirms "I sent a request". The page shows "Requested by N people" for that field.

### Flow 5. Report an error

1. Resident taps "Something wrong?" on a facility page.
2. Selects the field, describes the problem, optionally adds a source link and email.
3. Report goes to the curator queue. The resident sees a confirmation and expected response time.
4. Curator checks it, fixes the data if confirmed, and the change appears in the public corrections log.

### Flow 6. Curator adds or updates a facility (internal)

1. Curator imports or refreshes locations from the council's open data hub.
2. Adds cost, decision, maintainer and works records, each linked to a source document (URL, page, date).
3. Runs validation. Errors (missing source, wrong financial year format, coordinates outside LGA) block publishing.
4. Previews the change, publishes. The facility's "Last checked" date updates.

### Flow 7. Council publishes its own data (Phase 2)

1. Council staff download the import template.
2. Fill it from their asset register and finance system exports.
3. Upload, review validation results, fix errors.
4. Publish. Records show a "Verified by council" badge and the council's own sources.

---

## 8. Functional Requirements

Priority: **P0** must have for MVP, **P1** should have (soon after launch), **P2** nice to have.

### 8.1 Discovery

| ID | Requirement | Priority | User value | Acceptance criteria |
|---|---|---|---|---|
| FR-001 | Show all published facilities in the LGA on an interactive map, with a marker per facility that combines category colour, category icon and an accessible name. | P0 | Find places visually | Every published facility appears once at its coordinates. Markers are distinguishable without colour (icon) and have an accessible name "Name, Category". |
| FR-002 | Provide a list view with the same facilities and the same filters, usable without the map. | P0 | Inclusive access, faster scanning | List and map always show the same set. List works with keyboard and screen reader and if map tiles fail. |
| FR-003 | Filter by category (multi-select chips with counts). | P0 | Narrow down | Toggling a category updates map, list and summary within 200 ms. Counts reflect the full dataset. |
| FR-004 | Search by facility name, suburb, address or category name. | P0 | Find a known place fast | Matching is case-insensitive and tolerant of partial words. Zero results show a message and a "Show all places" action. |
| FR-005 | Sort the list by name, yearly cost, build cost, age and cost per visit. | P1 | Explore patterns | Facilities with no value for the sort field appear last, labelled "Not published". |
| FR-006 | Show a summary for the current selection: number of places, total yearly running cost where published, and how many places that total covers. | P0 | Context at a glance | Summary states coverage, e.g. "$14.2 million a year across 41 of 64 places (23 not published)". Totals never mix financial years (see FR-032). |
| FR-007 | "Near me": centre the map on the user's location and sort by distance, only after explicit permission. | P1 | Local relevance | Permission is requested only on tap. Denial shows a message and the app works normally. Location is never stored or sent. |

### 8.2 Facility page

| ID | Requirement | Priority | User value | Acceptance criteria |
|---|---|---|---|---|
| FR-010 | Header with name, category, suburb, address and status (Open, Temporarily closed, Under construction, Closed permanently). | P0 | Know you are on the right place | Status other than Open shows a banner with dates where known. |
| FR-011 | Key facts: year opened and age, condition rating with date assessed, visits per year with year. | P0 | Quick overview | Each fact shows "Not published" when missing. Condition uses the council's own scale label plus plain words (e.g. "3 of 5: Fair"). |
| FR-012 | Build cost: original build or last major works, with year and what it covered. | P0 | Know the investment | Shows amount, financial year, scope note and source link. If original and later works are both known, both are listed. |
| FR-013 | Yearly running cost: operating and maintenance cost for a named financial year, with what it includes. | P0 | Core answer | Shows amount, financial year, scope (e.g. "staff, energy, cleaning, repairs") and source. If only a service-level figure exists, it is shown separately and labelled as such, never as the facility's own cost. |
| FR-014 | Breakdown of yearly running cost by category where published. | P1 | Understand drivers | Bars are proportional, values labelled. Hidden entirely when no breakdown exists. |
| FR-015 | Everyday terms: yearly cost per resident and per visit, each with a one-line explanation of how it is calculated. | P0 | Make numbers meaningful | Per resident = yearly cost / LGA resident population (stated year and source). Per visit = yearly cost / visits in the same year. Not shown if the inputs are from different years. |
| FR-016 | Compare yearly cost with similar facilities in the same LGA. | P1 | Is this high or low? | Only compares within a defined sub-type (e.g. outdoor 50 m pools). Requires at least 3 comparable facilities with published costs for the same year; otherwise hidden. |
| FR-017 | "Why it is here": short plain-English explanation of the location and need. | P0 | Understand the reasoning | Every statement links to at least one source. Max 120 words. Written under the editorial policy (FR-037). |
| FR-018 | "How it was decided": date, decision body, resolution or reference number, summary, number of people consulted if published, link to minutes or business paper. | P0 | Accountability | Resolution reference and link are required to publish this section; otherwise the section shows "Decision record not found yet". |
| FR-019 | "Who looks after it": council team or contractor, what they do, contract value and end date where published in the contracts register. | P0 | Know who is responsible | Contractor names only from public sources (contracts register, council papers). Shows the register entry as source. |
| FR-020 | "History and planned works": timeline of opening, major works and planned works with year and cost. | P0 | See past and future | Planned works show the source (e.g. Operational Plan 2026-27) and are marked "Planned". Past dates cannot be marked planned. |
| FR-021 | "What is there": features and accessibility features. | P1 | Practical info | Uses a controlled list of features so they are consistent across facilities. |
| FR-022 | Directions link to the user's default maps app. | P1 | Get there | Opens in a new tab with destination coordinates. |
| FR-023 | Every facility has a stable, shareable URL that renders the facility page directly, with a link preview (title, summary, image). | P0 | Share a point | URL survives data updates. Shared link preview shows name and yearly cost (or "cost not published"). |
| FR-024 | Link to the council's own facility page and the place to report a maintenance problem. | P0 | Act on problems without building reporting | Each facility has a council URL. The "Report a problem with this place" link opens the council's channel, clearly labelled as leaving the site. |

### 8.3 Trust and data transparency

| ID | Requirement | Priority | User value | Acceptance criteria |
|---|---|---|---|---|
| FR-030 | Source citation for every figure and factual claim. Tapping "Source" shows document title, publisher, date, page or section and a link. | P0 | Trust and verification | Validation blocks publishing any figure without a source. Links open the document (or the page anchor where possible). |
| FR-031 | Data status per field: Published (with source), Not published by council, Requested, Verified by council (Phase 2). | P0 | Honest about gaps | Every displayed field has exactly one status. "Not published" never shows a zero or a dash. |
| FR-032 | Every money figure shows its financial year (format "2024-25"). Totals and ratios only combine figures from the same financial year. | P0 | Avoid misleading sums | Summary totals group by year; if a selection spans years, the summary shows the most common year and notes the rest. |
| FR-033 | "Last checked" date per facility, and a visible notice when data is older than 18 months. | P0 | Know how current it is | Notice appears automatically based on the date. |
| FR-034 | "How this works" page: data sources, methods (per resident, per visit, comparisons), editorial policy, corrections policy, who runs the site and how it is funded. | P0 | Credibility | Linked from every page footer and from each calculated figure. |
| FR-035 | Independence notice in Phase 1: "Independent project, not run by or affiliated with [Council]". | P0 | Avoid confusion with official sites | Visible in the header area on every page. No council logos or branding. |
| FR-036 | Public corrections log: date, facility, field, what changed, why. | P0 | Accountability for errors | Every published correction appears within 1 business day of the fix. |
| FR-037 | Editorial policy for narrative fields: neutral language, attribution ("The council's 2010 report says..."), no opinion, right of reply for the council. | P0 | Political neutrality | Policy is published. Curator checklist enforces it before publishing narrative text. |

> **Product concern: per-resident figures can mislead.** Rates are only part of council income, and many users of city facilities are not residents (CBD workers, visitors). **Recommendation:** keep "per resident" because it is the most relatable number, but label it "about $X per resident per year" and explain in one line that it divides the cost by the number of residents and does not mean each resident pays it directly. "Per visit" is the more accurate measure of value and should sit next to it.

> **Product concern: comparisons can be unfair.** A 50 m indoor aquatic centre and a small outdoor pool are not comparable. **Recommendation:** compare only within defined sub-types and only with enough facilities (FR-016), or not at all.

### 8.4 Feedback and action

| ID | Requirement | Priority | User value | Acceptance criteria |
|---|---|---|---|---|
| FR-040 | "Something wrong?" error report: field, description, optional source link, optional email. | P0 | Fix mistakes fast | Submission confirms receipt and states the response target (5 business days). Spam protection does not use inaccessible CAPTCHAs. |
| FR-041 | "Request this information" for any field marked Not published: plain explanation of informal request and GIPA, pre-written request text, links to the council's contact and access pages, optional "I sent a request" confirmation. | P0 | Turn gaps into action | Request text names the facility and the field. "Requested by N people" updates within 24 hours of confirmations. No personal data stored for the count. |
| FR-042 | "Was this page easy to understand?" yes/no with optional comment. | P0 | Measure clarity | One vote per page view session. Comment limited to 500 characters. |
| FR-043 | Newsletter or update sign-up for "new places added" (email only). | P2 | Return visits | Double opt-in. Unsubscribe in every email. |

### 8.5 Data operations (internal)

| ID | Requirement | Priority | User value | Acceptance criteria |
|---|---|---|---|---|
| FR-050 | Store the dataset in a versioned, structured format with a published schema. Every change is attributable and reversible. | P0 | Reliable data | Change history shows who changed what and when. Any version can be restored. |
| FR-051 | Import facility locations and attributes from the council's open data hub, matching on the council's facility ID. | P0 | Less manual work | Re-import updates changed records and flags new and removed facilities for review instead of deleting them. |
| FR-052 | Validation before publish: required fields, source on every figure, financial year format, coordinates inside the LGA, no duplicate IDs, amounts positive, dates not in the future unless "planned". | P0 | Catch mistakes | Publishing is blocked until validation passes. Errors name the facility and field. |
| FR-053 | Preview a change before publishing; publish updates the live site within 15 minutes. | P0 | Safe releases | Preview URL shows the exact change. Live site updates without downtime. |
| FR-054 | Curator queue for error reports and data requests, with status (New, Checking, Fixed, Not an error). | P0 | Close the loop | Every report has a status. Reporters who left an email get the outcome. |
| FR-055 | Source document archive: store a copy or archived link of each source document. | P1 | Links break | Each source has an archived copy or web archive URL in addition to the live link. |

### 8.6 Council features (Phase 2)

| ID | Requirement | Priority | User value | Acceptance criteria |
|---|---|---|---|---|
| FR-060 | Import template (CSV/XLSX) for councils, with documentation mapping common asset register and finance exports to the schema. | P1 | Councils can publish without a project | A council can populate 20 facilities in under a day using the template. |
| FR-061 | "Verified by council" status for records supplied by the council. | P1 | Official figures | Badge appears only on records imported by an authenticated council user. |
| FR-062 | Council right of reply: a short statement attached to a facility or field. | P1 | Fairness during the independent phase | Statement is labelled as the council's, dated, and cannot replace sourced data. |
| FR-063 | Council admin access with role-based permissions (viewer, editor, publisher). | P2 | Self-service | Only publishers can publish. All actions logged. |
| FR-064 | Embeddable facility card for council websites. | P2 | Reach residents where they already are | Embed meets the same accessibility requirements. |

---

## 9. UX / UI Requirements

### 9.1 Screens

| Screen | Purpose | Notes |
|---|---|---|
| Home (map + list) | Discover and filter places | Desktop: list panel left, map right. Mobile: map on top, list in a bottom sheet that can be dragged up. |
| Facility page | All information about one place | Same panel/sheet as the list, with "All places" back action. Has its own URL. |
| Source panel | Show where a figure comes from | Opens in place (popover on desktop, sheet on mobile). |
| Request information panel | Explain and pre-write a request | Must explain GIPA in one or two plain sentences. |
| Report an error form | Collect corrections | Short form, field pre-selected when opened from a field. |
| How this works | Methods, sources, editorial and corrections policy, independence | Plain language, with a glossary. |
| Corrections log | Public list of changes | Filterable by facility. |
| Place not found | Wrong or old links | Search and list available. |

### 9.2 Key components

- Category chip (icon + label + count), map marker (icon + colour), list item (name, type, suburb, age, yearly cost or "Not published").
- Money card (amount, label, financial year, source link), everyday-terms callout, breakdown bars, comparison bars.
- Data status label (Published, Not published by council, Requested by N, Verified by council).
- Timeline (past and planned, visually distinct, with text labels, not colour alone).
- Freshness notice, status banner, independence notice.

### 9.3 Navigation

- One page per facility with a real path (e.g. `/places/prince-alfred-park-pool`) so links work, search engines index it and link previews show the right content. **Recommendation:** move from the prototype's `#hash` links to real paths for SEO and sharing.
- Escape closes the facility page; focus returns to the list item that opened it.
- Browser back button works between list and facility page.

### 9.4 States

| State | Behaviour |
|---|---|
| Loading | List skeleton appears first; map loads after. Content is usable before the map finishes. |
| Empty search or filter | "No places match" with "Show all places". |
| Field not published | Data status label plus "Request this information". Never a blank or zero. |
| Whole section missing | Short explanation (e.g. "We have not found a decision record for this place yet") and "Know where to find it? Tell us". |
| Map tiles fail | Notice above the map; list unaffected. |
| Offline or network error | Already loaded pages stay readable; a banner explains the connection issue. |
| Location permission denied (P1) | Message with how to enable it; no repeated prompts. |
| Submission success/failure | Clear confirmation; on failure, keep the user's text and offer retry. |

### 9.5 Content rules

- Plain English following the Australian Government Style Manual. **Recommendation:** aim for a reading level around Year 7 and check every narrative field with a readability tool.
- Money format: "$1.9 million", "$420,000", "$8.26", "21 cents". No "k" or "m" in sentences; short forms only in tight list cells.
- Always name the financial year next to money.
- Avoid accounting terms on the main page. Use "cost to build" not "capital expenditure", "cost to run each year" not "opex". Keep the technical term in the glossary.

---

## 10. Data Requirements

### 10.1 Entities

| Entity | Key attributes | Notes |
|---|---|---|
| **Council** | id, name, state, population (value, year, source), contact URL, access to information URL, issue reporting URL, data licence | Population drives per-resident figures |
| **Facility** | id (stable), council facility ID, name, category, sub-type, address, suburb, coordinates, status, opened year, council page URL, features[], accessibility[], last checked date, parent facility id | Parent lets a pool sit inside a park |
| **CostRecord** | facility id or service id, type (build, major works, yearly running, yearly maintenance), amount (AUD), GST basis, financial year, scope description, breakdown[], source id, data status | Service-level records are linked to a category, not a facility |
| **UsageRecord** | facility id, visits, financial year, source id | Needed for per-visit figures |
| **ConditionRecord** | facility id, rating, scale (e.g. 1 to 5), assessed date, source id | Use the council's scale |
| **Decision** | facility id, date, decision body, reference, summary, consultation count, source id | One facility can have several decisions |
| **Maintainer** | facility id, type (council team, contractor), name, role description, contract value, start, end, contracts register reference, source id | Contractor names only from public sources |
| **Work** | facility id, description, status (completed, planned), year, cost, source id | |
| **Narrative** | facility id, type (why here), text, source ids[], author, reviewed date | Subject to editorial policy |
| **Source** | id, title, publisher, document date, URL, page or section, archived URL, accessed date, type | Types: open data, operational plan, financial statements, business paper, minutes, contracts register, GIPA response, council web page, media release, council-supplied |
| **FieldStatus** | entity, field, status (published, not published, requested, verified), request count | |
| **Report** | id, facility id, field, description, source link, email (optional), status, outcome, dates | Personal data: optional email only |
| **Correction** | id, facility id, field, old value, new value, reason, date | Public |

### 10.2 Relationships

- Council 1 to many Facility. Facility 0 to many of each record type. Every record 1 to 1 or more Source.
- Facility may have a parent Facility (a pool inside a park).
- A contract can cover several facilities (e.g. one operator for two pools): Maintainer links to many facilities and the page explains costs may be shared.

### 10.3 Validation rules

- No figure without a source. No narrative without at least one source.
- Financial year format `YYYY-YY`. Amounts are positive numbers, stored in whole dollars, with GST basis stated where known.
- Coordinates inside the LGA boundary.
- Planned works must have a year equal to or later than the current financial year.
- Per-visit and per-resident figures are calculated, never entered by hand.

### 10.4 Freshness

| Data | Expected refresh |
|---|---|
| Facility list and locations | Monthly import from open data hub |
| Yearly running costs, usage | Annually, after the council's annual report and financial statements (usually by November) |
| Planned works | Annually, after the Operational Plan is adopted (usually June) |
| Contracts | Quarterly check of the contracts register |
| Decisions | As found; full review annually |

### 10.5 Ownership and licensing

- **Phase 1:** the project owns the curated dataset; underlying facts belong to their publishers. Open data is used under its licence with attribution (City of Sydney publishes under Creative Commons licences; confirm the licence per dataset). **Recommendation:** publish the curated dataset under CC BY 4.0 to build trust and goodwill.
- **Phase 2:** council-supplied data remains the council's. The contract must allow display and redistribution under an open licence.

---

## 11. Technical Requirements

Only what is needed. The prototype (static HTML, CSS, JavaScript with Leaflet) is a reasonable base.

| Area | Requirement |
|---|---|
| **Platform** | Responsive website, mobile first. Supported: last 2 versions of Chrome, Safari (iOS and macOS), Edge, Firefox; Android Chrome. |
| **Rendering** | Pre-render each facility page to HTML at build time from the dataset, so content works without JavaScript, loads fast and is indexable. JavaScript adds the map, filters and panels. |
| **Data store** | Phase 1: structured files (or a lightweight database) under version control, validated against a schema at build time. Phase 2: a database with an admin interface and audit log once councils edit directly. |
| **Hosting** | Static hosting with a CDN. **Recommendation:** an Australian region or Australian-owned provider for Phase 2, because councils often require Australian data hosting. |
| **Maps** | Map library (Leaflet is sufficient). Base map tiles from a provider whose terms allow production use. **Product concern:** the prototype uses the public OpenStreetMap tile servers, whose usage policy does not allow heavy or commercial use. Use a paid tile provider or self-hosted vector tiles before launch. |
| **Geodata** | Council open data hub (ArcGIS feature services) for locations and attributes, with attribution. |
| **Forms** | Error reports, data request confirmations and understandability votes go to a small serverless endpoint or form service that writes to the curator queue. |
| **Analytics** | Cookieless, privacy-friendly analytics with no cross-site tracking (Section 13). |
| **Search** | Client-side search over the facility index is enough for up to a few thousand facilities. |
| **Authentication** | None for residents. Phase 2: council user accounts with role-based access; support the council's single sign-on if required by procurement. |
| **Notifications** | None in MVP. |
| **Offline** | Not required. Loaded pages stay readable. |

---

## 12. Non-Functional Requirements

| ID | Area | Requirement |
|---|---|---|
| NFR-001 | Performance | Largest Contentful Paint at or under 2.5 s (75th percentile) on a mid-range Android phone on 4G. Facility list usable before the map loads. |
| NFR-002 | Performance | Initial JavaScript at or under 150 KB compressed, excluding map tiles. |
| NFR-003 | Reliability | 99.5% monthly availability. If forms fail, users see a message and their text is kept. |
| NFR-004 | Scalability | MVP: 1 LGA, up to 200 facilities, up to 50,000 visits a month. Phase 2: up to 50 councils and 20,000 facilities without architecture change. |
| NFR-005 | Security | HTTPS only, security headers, dependency scanning. Forms rate limited. Phase 2: role-based access, audit log, MFA for council publishers. |
| NFR-006 | Privacy | Collect no personal information except an optional email on reports. No location stored. Privacy statement published. Phase 2 contracts must address the NSW PPIP Act (which applies to councils, including mandatory data breach notification) or the equivalent state law. |
| NFR-007 | Accessibility | WCAG 2.2 AA. Tested with keyboard, VoiceOver (iOS, macOS), TalkBack and NVDA before launch and after major releases. Colour never the only way to convey meaning. Touch targets at least 44 by 44 px. Respects reduced motion and dark mode. |
| NFR-008 | Content quality | Every narrative field reviewed against the editorial policy and readability target before publishing. |
| NFR-009 | Maintainability | Adding a new council requires configuration and data only, no code changes. |

---

## 13. Analytics and Events

Only events that answer a product question. No personal data, no cross-site tracking.

| Event | Trigger | Important properties | Purpose |
|---|---|---|---|
| `facility_opened` | Facility page displayed | facility_id, category, entry (map, list, search, shared link, search engine) | Which places and entry points matter |
| `cost_section_viewed` | Money section is at least 50% visible for 2 s | facility_id, cost_status (published, not published) | Primary metric |
| `source_opened` | Source panel opened | facility_id, field, source_type | Do people check sources? Which ones? |
| `filter_changed` | Category toggled | category, state | Category interest |
| `search_performed` | Search submitted or paused 1 s | result_count, query text only when result_count = 0 (truncated to 40 characters) | Find missing places and vocabulary gaps |
| `share_clicked` | Copy link or share used | facility_id | Spread and advocacy |
| `council_link_clicked` | Report a problem or council page link | facility_id, link_type | Value as a gateway to council services |
| `data_request_started` | Request panel opened | facility_id, field | Demand for missing data |
| `data_request_confirmed` | "I sent a request" | facility_id, field | Pressure created for publishing |
| `error_report_submitted` | Report sent | facility_id, field | Data quality signal |
| `understandability_vote` | Yes/No pressed | facility_id, value | Clarity |
| `map_failed` | Tiles or map library error | error_type | Reliability |

---

## 14. Success Metrics

Targets are first estimates for the pilot LGA and should be reset after the first full month of data.

### Primary metric

| Metric | Definition | Target | Measurement |
|---|---|---|---|
| **Residents informed** | Monthly unique visitors who trigger `cost_section_viewed` at least once | 2,000 in month 3 after launch; 6,000 in month 6 | Analytics, monthly |

Why this one: it measures the core value (a person saw what a place costs), not just visits.

### Secondary metrics

| Metric | Definition | Target |
|---|---|---|
| Understandability | Share of "Yes" in `understandability_vote` (min. 200 votes) | 80% or more |
| Source checking | Share of cost views followed by `source_opened` | 5% to 15% (signals trust checking without confusion) |
| Sharing | Facility pages opened from shared links per month | Growing month on month |
| Data coverage | Share of MVP facilities with a published yearly running cost | Baseline at launch, then +10 points per year |
| Data requests | `data_request_confirmed` per month | 50 or more by month 6 |
| Council pipeline | Councils in active conversation / signed pilot or LOI | 5 conversations and 1 signed within 9 months |

### Guardrail metrics

| Metric | Threshold |
|---|---|
| Confirmed factual errors | 2 or fewer per 100 facilities per quarter; median fix time 5 business days or less |
| Unsourced figures live | Zero (validation enforced) |
| Accessibility | Zero open WCAG 2.2 AA failures |
| Performance | LCP p75 at or under 2.5 s |
| Formal complaints (council, contractor, legal) | Zero unresolved after 10 business days |

---

## 15. Edge Cases and Failure States

Ordered by impact.

| Case | Impact | Handling |
|---|---|---|
| Wrong figure published | High (trust, legal) | Validation, source on every figure, error reports, public corrections log, fix target 5 business days; urgent fixes within 1 business day if flagged by council or a named party |
| Cost published only for a group (all pools, all libraries) | High (core content) | Show the group figure separately, labelled "council-wide", never divided by facility count unless the council publishes that method |
| One contract covers several facilities | Medium | Show contract once per facility with "This contract also covers: X, Y" |
| Figures from different financial years | Medium | Each figure keeps its year; totals and ratios only within the same year (FR-032) |
| GST inclusive vs exclusive figures | Medium | Store GST basis; show note if unknown; never add mixed bases |
| Facility inside another (pool in a park) | Medium | Parent/child; both clickable; parent page lists children |
| Facility closed, under construction or demolished | Medium | Status banner; demolished facilities hidden from map but URL shows a "closed" page with history |
| Source link breaks | Medium | Archived copy (FR-055); periodic link check |
| Council disputes content | Medium | Right of reply (FR-062), review within 5 business days, note in corrections log |
| Open data import changes IDs or removes facilities | Medium | Flag for review, never auto-delete |
| Map tiles or library fail | Medium | List remains usable, notice shown |
| Data older than 18 months | Low to medium | Automatic freshness notice |
| Search typo or local name ("Ian Thorpe pool") | Low | Partial and alias matching; zero-result queries logged |
| Location permission denied (P1) | Low | Works without location |
| Spam on forms | Low | Rate limits and honeypot field; no inaccessible CAPTCHA |
| JavaScript disabled | Low | Pre-rendered facility pages and list readable |

---

## 16. Acceptance Criteria

**Discovery**
- Given the home page has loaded, when the user unchecks "Pools", then pool markers and pool list items disappear and the summary updates its count and total.
- Given the user searches "zetland", when results load, then only facilities in Zetland or matching "zetland" in name or address are listed and the count is announced to screen readers.
- Given a search with no matches, when results load, then a message and a "Show all places" button appear.

**Facility page**
- Given a facility with a published yearly running cost for 2024-25, when the page opens, then the amount, "2024-25", the scope and a Source link are shown.
- Given a facility with no published yearly running cost, when the page opens, then the money card shows "Not published by the council" and a "Request this information" button, and no zero or dash.
- Given a yearly cost and visit numbers from different financial years, when the page opens, then the per-visit figure is not shown.
- Given fewer than 3 comparable facilities with costs for the same year, when the page opens, then the comparison block is not shown.
- Given a decision record without a resolution reference, when the curator tries to publish, then validation blocks it.
- Given a facility URL is shared, when someone opens it, then the facility page renders directly with the map centred on it.

**Trust**
- Given any figure on a facility page, when the user taps Source, then the document title, publisher, date, page or section and link are shown.
- Given a facility last checked more than 18 months ago, when the page opens, then a freshness notice is shown.
- Given a confirmed error report, when the fix is published, then a correction entry appears in the public log within 1 business day.

**Feedback**
- Given a "Not published" field, when the user opens "Request this information", then the pre-written text names the facility and the field and links to the council's contact and access pages.
- Given a user submits an error report without email, when it is sent, then they see a confirmation and the report appears in the curator queue with status "New".

**Accessibility**
- Given a keyboard-only user, when they tab through the page, then every interactive element is reachable, focus is visible and Escape closes the facility page returning focus to the list item.
- Given a screen reader user on the list, when they open a facility, then focus moves to the facility heading.

---

## 17. MVP Scope

| Feature | Priority | MVP? | Reason |
|---|---|---|---|
| Map with category markers (FR-001) | P0 | Yes | Core entry point |
| List view, filters, search (FR-002 to FR-004) | P0 | Yes | Inclusion and speed |
| Summary with coverage (FR-006) | P0 | Yes | Context and honesty about gaps |
| Facility page core: header, facts, build cost, yearly cost, everyday terms, why here, decision, maintainer, history and planned works (FR-010 to FR-013, FR-015, FR-017 to FR-020) | P0 | Yes | The product's main value |
| Shareable URLs and council links (FR-023, FR-024) | P0 | Yes | Spread and action without building reporting |
| Sources, data status, financial year rules, freshness, method page, independence notice, corrections log, editorial policy (FR-030 to FR-037) | P0 | Yes | Credibility is the product |
| Error reports, data requests, understandability vote (FR-040 to FR-042) | P0 | Yes | Data quality and demand signal |
| Data operations: versioned data, import, validation, preview, queue (FR-050 to FR-054) | P0 | Yes | Without it the data rots |
| Sort (FR-005) | P1 | No | Useful, not essential at 60 to 100 facilities |
| Cost breakdown, comparison (FR-014, FR-016) | P1 | No | Data rarely available; misleading if thin |
| Near me, features list, directions (FR-007, FR-021, FR-022) | P1 | No | Nice for usability, not core value |
| Source archive (FR-055) | P1 | No | Needed within months, not day one |
| Council import, verified badge, right of reply (FR-060 to FR-062) | P1 | No | Phase 2; right of reply may be brought forward if a council objects |
| Council admin portal, embed, newsletter (FR-063, FR-064, FR-043) | P2 | No | After first paying council |

**MVP content scope:** City of Sydney; aquatic and leisure centres, libraries, community and recreation centres, and major parks (named parks with facilities such as playgrounds, sports fields or amenities). Target 60 to 100 facilities. **Recommendation:** do not include all 400+ parks; pocket parks have little cost data and add curation load without much resident value.

> **Product concern: the prototype shows data that likely does not exist publicly.** The prototype displays yearly running costs, breakdowns, visits and consultation counts for every facility. Research suggests most of these are not published per facility. If the MVP launches with mostly "Not published" labels, the experience changes. **Recommendation:** before building, run a 2-week data audit on 20 facilities to measure real coverage per field (see Section 20, Q1). Design the facility page so it is still useful with only location, history, decisions, contracts and council-wide costs.

---

## 18. Future Opportunities

Intentionally outside the MVP:

- Additional councils, starting with councils facing rate rise debates where demand for clarity is high.
- Suburb view: what is spent in my suburb compared with the LGA.
- Alerts for planned works or closures at places a resident follows.
- Translations into the top community languages of each LGA.
- Public API and bulk download of the curated dataset.
- Integration with council asset systems for automatic updates (Phase 2+).
- Embeddable cards for council consultation pages, including special rate variation consultations.
- Condition and renewal backlog view per facility, when councils publish it.
- Links to consultation platforms when a facility has an open consultation.

---

## 19. Risks and Assumptions

### Assumptions to validate

| Assumption | How to validate | When |
|---|---|---|
| Enough public data exists to make facility pages useful | 2-week data audit of 20 facilities, measuring coverage per field | Before build |
| Residents will use it when triggered | Launch with 20 facilities and promote in 2 local channels; measure Residents informed | Month 1 to 3 |
| Plain-language pages are understood | 5 to 8 moderated usability sessions, including people with low numeracy and assistive technology users | Before launch |
| Councils will pay for a publishing layer | 10 discovery interviews with council communications, engagement and asset staff; test willingness to pay | Months 1 to 6 |
| Visible gaps create pressure, not hostility | Track council responses and data requests; interview 2 councils about the "Not published" labels | Months 3 to 6 |

### Risks

| Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|
| Per-facility cost data is mostly unavailable | High | High | Data audit first; council-wide figures as context; data requests; Phase 2 council data; design for partial data |
| Errors damage trust or create legal exposure (e.g. about contractors) | Medium | High | Source on every figure, only public contractor information, corrections log, fast fixes, legal review of editorial policy, professional indemnity and media liability insurance |
| Pilot council sees the independent site as hostile | Medium | High | Neutral tone, early briefing before launch, right of reply, no branding, position as an ally in transparency |
| Perceived political bias, especially during rate debates or elections | Medium | High | Editorial policy, attribution, no opinion, publish who runs and funds the site |
| Data curation cost is higher than expected (PlanningAlerts showed that scrapers break often) | High | Medium | Narrow scope, scheduled refresh calendar, import tooling, prioritise councils that supply data |
| Low resident demand outside trigger moments | Medium | Medium | Optimise for search and sharing; partner with local media and resident groups during budget and rate consultations |
| Long council sales cycle (procurement, budgets) | High | Medium | Start conversations in Phase 1; price under council quotation thresholds for a first pilot; target the budget cycle |
| Map tile terms or costs | Medium | Low | Use a production tile provider or self-hosted tiles; budget for it |
| Confusion with an official council site | Low | Medium | Independence notice, no council branding |

---

## 20. Open Questions

| # | Question | Priority | Why it matters |
|---|---|---|---|
| Q1 | What share of MVP facilities have a published yearly running cost, visits and decision record? | Critical | Decides whether the core value is deliverable in Phase 1 |
| Q2 | Who funds Phase 1, and is the project run as a company or a not-for-profit? | Critical | Affects credibility, grants, insurance and council relationships |
| Q3 | Which council is the first Phase 2 target? The pilot area (City of Sydney) may not be the best buyer. | Critical | Focus of discovery interviews and feature priorities |
| Q4 | Who owns the editorial policy and signs off narrative content? Is legal review needed before launch? | Critical | Legal and reputational risk |
| Q5 | Should the pilot council be briefed before launch? | Important | Relationship and right of reply |
| Q6 | Final product name and domain (avoid anything that sounds official) | Important | Trust and clarity |
| Q7 | Pricing model for councils (per council per year, by population band, or setup plus subscription) | Important | Phase 2 business case |
| Q8 | Which resident population figure to use (ABS estimated resident population, year)? | Important | Per-resident figures |
| Q9 | Should the curated dataset be openly licensed from day one? | Nice to resolve | Goodwill and reuse |

---

## Appendix A. Evidence and Sources

Research carried out in October 2026. Some sources are secondary (news, vendor or council pages) and are marked as such.

**Sector size and assets**
- ALGA, Facts and figures (537 councils, about A$48 billion expenditure 2023-24): https://alga.com.au/about/local-government/facts-and-figures/
- ALGA, 2026 National State of the Assets report launch: https://alga.com.au/launch-of-the-2026-national-state-of-the-assets-report/
- Inside Local Government, "ALGA report highlights $280 billion infrastructure renewal challenge" (secondary): https://insidelocalgovernment.com.au/alga-report-highlights-280-billion-infrastructure-renewal-challenge/
- Inside Local Government, NSW Audit Office local government financial audit 2026 (secondary): https://insidelocalgovernment.com.au/?p=33871

**What councils publish (NSW and Victoria)**
- NSW OLG, Integrated Planning and Reporting Guidelines 2021: https://www.olg.nsw.gov.au/wp-content/uploads/2023/09/IPR-Guidelines-2021.pdf
- Byron Shire, State of assets report (example of condition and required maintenance reporting): https://www.byron.nsw.gov.au/files/assets/public/hptrim/property-management-council-properties-asset-management-roads-20212022/strategic-asset-management-plan-2022-state-of-assets-report.pdf
- City of Newcastle, Calculation of infrastructure in need of renewal (backlog not audited): https://ncc.nsw.gov.au/about-us/news-and-updates/projects-and-works/calculation-of-infrastructure-in-need-of-renewal
- Northern Beaches Council, Contracts register (GIPA, $150,000 threshold): https://www.northernbeaches.nsw.gov.au/council/tenders/contracts-register
- City of Greater Geelong, Public Transparency Policy (Local Government Act 2020, s57 and s58): https://www.geelongcity.vic.gov.au/council/legislation-and-local-laws/governance-policies-and-transparency/public-transparency-policy

**Existing alternatives**
- NSW OLG, Your Council: https://yourcouncil.nsw.gov.au and https://www.olg.nsw.gov.au/public/your-council-data-and-reports
- Know Your Council, Local Government Performance Reporting (data.vic): https://discover.data.vic.gov.au/dataset/local-government-performance-reporting
- VAGO, Local government performance reporting presentation (2019): https://www.audit.vic.gov.au/sites/default/files/2019-05/20190523-LG-Performance-presentation_0.pdf
- Delib, Budget Simulator customers in Australia: https://www.delib.net/who_uses_delib/budget-setting-in-australia
- Livingstone Shire Council, Balancing Act budget tool: https://livingstone.qld.gov.au/news/article/117/how-would-you-balance-council-s-budget-residents-invited-to-have-their-say-with-new-budget-simulation-tool-
- ClearGov listing (Capterra, secondary): https://www.capterra.com.au/software/149444/cleargov
- Engagement Hub comparison of engagement platforms (competitor-authored, treat with care): https://engagementhub.com.au/?p=100057
- Snap Send Solve (Wikipedia, secondary): https://en.wikipedia.org/wiki/Snap_Send_Solve
- PlanningAlerts, About: https://www.planningalerts.org.au/about
- OpenAustralia Foundation, "PlanningAlerts: going back to basics": https://oaf.org.au/2010/05/07/planningalerts-going-back-to-basics/

**Demand and trust**
- APSC, Trust in Australian public services: 2025 Annual Report: https://www.apsc.gov.au/publication/trust-australian-public-services-2025-annual-report
- IPART, media release on 10 councils applying for 2026-27 special variations: https://www.ipart.nsw.gov.au/sites/default/files/cm9_documents/Media-Release-IPART-seeks-community-feedback-as-10-councils-apply-to-increase-rates-above-the-rate-peg-17-February-2026.PDF
- IPART, Final report on North Sydney Council special variation 2025-26: https://www.ipart.nsw.gov.au/sites/default/files/cm9_documents/Final-Report-North-Sydney-Council-Special-Variation-and-Minimum-Rate-Application-for-2025-26-May-2025.PDF
- IPART, ratepayer workshop summary (August 2024): https://www.ipart.nsw.gov.au/sites/default/files/cm9_documents/Fact-Sheet-Summary-of-discussion-at-ratepayer-workshop-13-August-2024.PDF

**Pilot area data**
- City of Sydney ArcGIS services directory (pools, libraries, council facilities and more): https://services1.arcgis.com/cNVyNtjGVZybOQWZ/ArcGIS/rest/services
- City of Sydney open data on Data.NSW: https://data.nsw.gov.au/data/dataset/5-cityofsydney--open-data
- City of Sydney media release on 2025/26 budget (over $900 million): https://news.cityofsydney.nsw.gov.au/media-releases/multi-billion-dollar-commitment-drive-urban-transformation-boost-facilities

**Accessibility, literacy and privacy**
- Australian Government Style Manual, accessibility responsibilities: https://www.stylemanual.gov.au/node/220
- Service NSW, accessibility standards: https://www.service.nsw.gov.au/accessibility
- Information Access Group, Australian literacy levels and PIAAC (secondary): https://informationaccessgroup.com/literacy-levels-in-australia/ and https://informationaccessgroup.com/news/2023-survey-of-adult-skills-results/
- Mondaq, NSW mandatory notification of data breach scheme for public sector agencies including councils (secondary): https://www.mondaq.com/australia/data-protection/1473632/legislators-up-the-stakes-on-privacy-with-new-mandatory-scheme-for-nsw-public-sector-agencies
- OpenStreetMap Foundation, Tile usage policy: https://operations.osmfoundation.org/policies/tiles/

**Gaps in the research**
- No official 2024 ABS population figure for the City of Sydney was retrieved (the prototype uses 230,000; Data.NSW cites over 215,000 in 2021). Confirm before launch (Q8).
- No independent market share data for council asset or transparency software in Australia was found.
- The Jobs and Skills Australia Foundation Skills Study (replacing PIAAC 2023 for Australia) was not checked.

---

## Appendix B. Prototype vs MVP

| Area | Prototype today | Needed for MVP |
|---|---|---|
| Data | 13 facilities, illustrative figures in a JS file | 60 to 100 facilities, real public data, schema, validation, sources |
| Missing data | Every field filled | Data status per field, "Not published" and request flow |
| Sources | One note in footer | Source on every figure, method page, corrections log |
| URLs | `#hash` per facility | Real paths, pre-rendered pages, link previews |
| Map tiles | Public OpenStreetMap servers | Production tile provider |
| Feedback | Buttons show a message only | Working error reports, data requests, votes, curator queue |
| Independence | "Prototype, sample data" badge | Independence notice and "How this works" page |
| Analytics | None | Events in Section 13 |
| Accessibility | Built to WCAG principles, not audited | Audit and assistive technology testing |
