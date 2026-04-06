# Designing with the Mind in Mind: Cognitive Accessibility in Enterprise Software

**Role:** Staff UX Researcher & Designer  
**Timeline:** 48-hour Design Hackathon → 6-week Implementation  
**Platform:** Enterprise Web Application  
**Recognition:** Internal Design Innovation Award — Accessibility Category  
**Status:** Completed  

---

## Table of Contents

1. [Overview](#overview)
2. [The Problem](#the-problem)
3. [The Constraint That Became the Concept](#the-constraint-that-became-the-concept)
4. [Research Foundation](#research-foundation)
5. [The Design Concept](#the-design-concept)
6. [Prototyping & Validation](#prototyping--validation)
7. [Key Decisions & Rationale](#key-decisions--rationale)
8. [Outcomes](#outcomes)
9. [Broader Implications](#broader-implications)
10. [What I Learned](#what-i-learned)
11. [Accessibility Design Principles Reference](#accessibility-design-principles-reference)

---

## Overview

This case study documents the design of a **cognitive accessibility intervention** for a high-density enterprise web application — conceived during a 48-hour internal design Hackathon and developed into a production-ready feature over the following six weeks.

The intervention — a **Panel Reading Mask** — is a zero-cost, zero-development-resource accessibility tool designed to support users with ADHD, dyslexia, and other attention-regulation differences when navigating complex, information-dense interface panels.

It won the organization's internal Design Innovation Award in the Accessibility category.

What makes this case study worth reading is not the complexity of the solution. It is the simplicity of it — and what that simplicity required to arrive at.

---

## The Problem

### The user population

Enterprise software users are not a homogeneous group. In any organization deploying a complex web application, a meaningful percentage of users will have attention-regulation differences — ADHD, dyslexia, visual processing differences, anxiety-related concentration challenges — that are invisible to the product team and unaccounted for in the design.

These users rarely self-identify. They develop workarounds. They take longer. They make more errors. They abandon features. And because their challenges are invisible, the product team interprets their behavior as a training problem, a motivation problem, or a complexity problem — not an accessibility problem.

### The interface context

The application in question contained dense data panels used for reviewing, comparing, and acting on multiple data points simultaneously. For neurotypical users with strong working memory, the panels were manageable — cognitively demanding, but navigable.

For users with ADHD or attention-regulation differences, the panels created a specific and recurring problem: **line-tracking failure**. When reading across a dense row of data, the eye loses its place — jumps to an adjacent row, skips a field, or loses context entirely. The user must restart. The cognitive cost compounds. Errors increase. Confidence erodes.

### Why existing solutions didn't fit

Common responses to dense interface problems include:

- **Reduce information density** — not viable when all data points are operationally necessary
- **Add pagination** — fragments workflows that require simultaneous comparison
- **Increase font size** — improves legibility but does not solve line-tracking failure
- **Change color contrast** — addresses visibility, not tracking
- **Provide training** — addresses skill, not cognitive difference

None of these solutions addressed the root cause: the absence of a visual anchor that helps the eye stay oriented within a dense horizontal row.

---

## The Constraint That Became the Concept

The Hackathon brief was deliberately open: **"Design something that makes this product more accessible."**

The real constraint was unstated but understood: any solution conceived in a 48-hour Hackathon would need to be implementable without significant engineering resources. A concept that required backend changes, new data infrastructure, or substantial frontend development would not survive the transition from Hackathon idea to production feature.

This constraint — **zero additional development cost** — became the generative pressure that produced the concept.

> *"If I can't add anything to the system, what can I give the user control over?"*

The answer: a transparent overlay. A reading mask. Something that already exists as a browser-native behavior that CSS and minimal JavaScript can produce — requiring no new data, no new API calls, no new backend logic.

The constraint eliminated a hundred ideas and left one that was exactly right.

---

## Research Foundation

### Literature review — cognitive accessibility

Prior to concept development, a focused literature review informed the design direction:

**Reading masks and line guides** have been used in physical reading aids for decades — transparent colored overlays placed over text to reduce visual crowding and help the eye track across a line. Research on their effectiveness for users with dyslexia and ADHD consistently shows improvement in reading accuracy and reduction in fatigue, even when users initially report skepticism about their usefulness.

**Visual crowding** — the interference of adjacent text or data on the legibility of a target — is a documented challenge for users with attention-regulation differences and is exacerbated by high information density environments like enterprise data panels.

**User control over accessibility tools** consistently improves adoption. Users are more likely to use an accessibility feature they can activate, adjust, and dismiss on their own terms than one that is applied universally or requires IT involvement to configure.

### Stakeholder signal gathering

Before the Hackathon, informal conversations with internal users and colleagues surfaced consistent patterns:

- Multiple users mentioned using a physical finger or pen to track across rows when reading dense data
- Several users described losing their place and having to restart row reads multiple times per session
- One user mentioned using a physical ruler held against their monitor screen
- No users had formally reported this as an accessibility concern — they had normalized the workaround

The workarounds were the signal. Users had already invented the solution in physical form. The design task was to bring it into the interface.

---

## The Design Concept

### The Panel Reading Mask

The Panel Reading Mask is a **user-activated, horizontally-anchored visual overlay** that highlights the row currently under the user's cursor within a dense data panel — dimming all other rows to create a clear visual focus band.

**How it works:**
- A small accessibility toggle activates the reading mask for any supported panel
- As the user moves their cursor vertically through the panel, the row under the cursor is highlighted with a soft, semi-transparent color band
- All other rows are dimmed to a reduced opacity — not hidden, but visually receded
- The highlight follows cursor movement smoothly, without snapping or lag
- The mask can be toggled off instantly with the same control

**What it does not do:**
- It does not change the data
- It does not change the layout
- It does not require the user to configure a profile or declare a disability
- It does not affect any other user's experience
- It does not require any backend change

### Design decisions at the concept stage

**Color selection for the highlight band**  
The highlight color needed to be distinct enough to serve as a visual anchor without introducing a new accessibility problem for users with color vision differences. The final concept used a warm neutral — a soft amber — that provides sufficient contrast in both light and dark mode without creating red/green confusion patterns.

**Opacity of the dimmed rows**  
The dimmed rows needed to be visually receded without becoming unreadable. Testing during prototyping identified 40% opacity as the threshold — enough to create a clear focal hierarchy without making context data inaccessible.

**Toggle placement**  
The accessibility toggle was placed at the panel level, not the application level — allowing users to activate it only where they need it, without committing to a global setting. This respected user autonomy and reduced the cognitive cost of trying and abandoning the feature.

**No profile requirement**  
The decision not to require users to identify themselves as having a disability or accessibility need was deliberate and non-negotiable. Accessibility features that require self-identification create a barrier that prevents the users who most need the feature from accessing it. The toggle is available to everyone, described neutrally as a "reading focus" tool.

---

## Prototyping & Validation

### Hackathon prototype — 48 hours

The Hackathon prototype was built as a CSS/JavaScript overlay applied to a static representation of the target panel. It demonstrated:

- The core highlight behavior
- The dimming effect on non-active rows
- The toggle activation mechanism
- Behavior across different row heights and data densities

The prototype was presented to the Hackathon evaluation panel with a live demonstration and a brief that included the research foundation, the constraint rationale, and the implementation pathway.

### Post-Hackathon validation — 6 weeks

Following the award, the concept moved into a structured validation phase:

**Round 1 — Internal usability testing**  
5 participants asked to complete row-reading tasks with and without the reading mask enabled. Measured: task completion accuracy, time on task, and subjective confidence rating.

Key findings:
- Task accuracy improved for 4 of 5 participants with the mask enabled
- Time on task reduced for all 5 participants
- All 5 participants rated their confidence higher with the mask enabled
- 2 participants who had not self-identified as having attention-regulation differences reported the mask "surprisingly helpful"

**Round 2 — Design critique with engineering**  
Presented the validated concept to the engineering team with implementation specifications. Confirmed zero backend dependency. Frontend implementation estimated at less than one sprint.

**Round 3 — Accessibility review**  
Reviewed the concept against WCAG 2.1 guidelines and internal accessibility standards. Confirmed the feature did not introduce new accessibility barriers and met contrast requirements in both active and dimmed states.

---

## Key Decisions & Rationale

### Decision 1 — Solve the physical workaround, not the stated complaint
**What:** Based the concept on observed workarounds (finger-tracking, ruler-on-monitor) rather than formally reported accessibility concerns.  
**Why:** Users with invisible disabilities rarely report their challenges through formal channels. The workaround is the complaint — it just hasn't been translated into product language yet. Designing for the workaround is designing for the actual user, not the reported user.

### Decision 2 — Make it universally available, not accessibility-gated
**What:** Placed the reading mask toggle in the standard panel interface, available to all users without self-identification.  
**Why:** Accessibility features that require declaration create two problems: they prevent adoption by users who need them but won't self-identify, and they stigmatize the feature for users who would benefit from it without considering themselves to have an accessibility need. Universal availability removes both barriers.

### Decision 3 — Panel-level activation, not application-level
**What:** The toggle activates per-panel, not globally across the application.  
**Why:** Global accessibility settings require users to commit to a persistent change they may not want everywhere. Panel-level activation respects that a user might need reading support in one dense context but not in simpler interfaces. It reduces the cost of trying.

### Decision 4 — Describe it as a "reading focus" tool, not an "accessibility" tool
**What:** The toggle label and tooltip use "reading focus" language rather than "accessibility" language.  
**Why:** Language shapes perception of who a feature is for. "Accessibility" signals to many users that the feature is not for them — that it is for someone with a disability, and they do not have a disability. "Reading focus" is descriptive, neutral, and accurate — and it invites the full user population to consider whether it might be useful.

---

## Outcomes

### Hackathon
- **Won** the internal Design Innovation Award — Accessibility Category
- Recognized by the evaluation panel for research grounding, constraint-informed design thinking, and implementation viability

### Post-implementation (measured at 90 days)
| Metric | Result |
|---|---|
| Feature adoption rate | 23% of panel users activated the reading mask at least once |
| Task accuracy (panel reading tasks) | +18% improvement in error rate for regular mask users |
| Support tickets related to panel data errors | −31% reduction in the 90 days following launch |
| User satisfaction with panel experience | +12 points on internal satisfaction survey |

### Qualitative signal
> *"I didn't realize how much mental energy I was spending just tracking rows. This is the first time this panel has felt manageable."*  
> — Internal user, post-launch feedback

> *"I don't have ADHD or anything, I just find it genuinely easier. Why didn't we have this before?"*  
> — Internal user, post-launch feedback

The second quote is the most important outcome. When a user who does not consider themselves to have an accessibility need finds an accessibility feature genuinely useful — that is universal design working exactly as intended.

---

## Broader Implications

### Cognitive accessibility is underserved in enterprise software
The enterprise software market has made significant progress on visual accessibility — color contrast, screen reader support, keyboard navigation. Cognitive accessibility — the design of interfaces that support users with attention-regulation differences, working memory limitations, and processing differences — remains largely unaddressed.

This is not because cognitive accessibility is less important. It is because cognitive accessibility challenges are less visible, less frequently reported, and less codified in compliance frameworks. The absence of a WCAG requirement does not indicate the absence of a user need.

### Zero-cost accessibility is possible more often than assumed
The most common objection to accessibility improvements is resource cost. The reading mask demonstrates that accessibility innovation does not always require significant engineering investment. Many of the most impactful cognitive accessibility improvements are interface-level — overlay behaviors, progressive disclosure patterns, focus management, reading order — that can be implemented with CSS and minimal JavaScript.

### Workarounds are a research method
If users are placing rulers on their monitors, using their fingers to track text, or opening the same panel in two windows to compare data — those behaviors are design research data. They are evidence of unmet needs that the product has not yet served. Systematic observation of workarounds is one of the highest-signal research activities available to a product team.

---

## What I Learned

**The constraint was the design.**  
The requirement that the solution cost nothing to implement did not limit the concept — it clarified it. Removing the option to add complexity forced the question: what can the user control that already exists? That question led directly to the right answer.

**Invisible disabilities require proactive design.**  
Users with ADHD, dyslexia, and related differences will not always tell you they are struggling. They will find workarounds, blame themselves, or quietly avoid the features that challenge them. Proactive cognitive accessibility design — designing for the full range of human attention and processing — is the only way to serve them.

**Universal design is not a compromise.**  
Making the reading mask available to all users without requiring self-identification did not dilute the feature for users with genuine accessibility needs. It amplified it — by removing the barrier to adoption and demonstrating that cognitive accessibility features benefit a much wider population than their primary audience.

**Small solutions earn large trust.**  
A feature that costs nothing to implement and genuinely improves the experience for users who needed it — and users who didn't know they needed it — builds more organizational trust in the design function than any high-budget redesign. Showing that design intelligence can find the right answer within real constraints is one of the most powerful things a designer can demonstrate.

---

## Accessibility Design Principles Reference

The following principles informed this case study and serve as a reference for cognitive accessibility design practice.

| Principle | Description | Application in this case study |
|---|---|---|
| Universal Design | Design for the full range of human ability, not the average user | Reading mask available to all users without self-identification |
| Progressive Disclosure | Reveal complexity only when needed | Panel-level toggle — activate only where needed |
| User Control | Give users control over their own experience | User-activated, user-dismissed, per-panel |
| Cognitive Load Reduction | Minimize unnecessary mental work | Dimming non-active rows reduces visual competition |
| Non-Stigmatizing Language | Describe features by what they do, not who they're for | "Reading focus" not "accessibility mode" |
| Workaround Observation | Treat user workarounds as unmet needs | Concept inspired by finger-tracking and ruler behaviors |
| Low Barrier to Try | Reduce the cost of engaging with a new feature | One-click toggle, no configuration, no commitment |
| WCAG Alignment | Meet established accessibility standards as a floor, not a ceiling | Contrast ratios validated in active and dimmed states |

---

## Support This Work

If this framework has been useful for your GovCon pursuits, consider buying me a coffee. It helps me keep building open source tools for the design and GovCon community.

☕ [Buy Me a Coffee](https://buymeacoffee.com/teamdesignstudios)

---

*Created by Susan E. Aldridge | [LinkedIn](https://www.linkedin.com/in/susanealdridge/) | [Portfolio](https://docsend.com/view/s/9bzhycnqab7k92nq)*  
*2024 UX Centric Award — Design Innovation, Accessibility Category*
