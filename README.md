# The Last Hero
## Game Design Document

| | |
|---|---|
| **Genre** | Narrative strategy / hall management |
| **Platform** | HTML5, single file, desktop and mobile browsers |
| **Session length** | 30 to 60 minutes per campaign |
| **Players** | Solo |
| **Status** | Playable proof of concept (`[the_last_hero.html](https://peterdsouza247.github.io/the-last-hero/)`) |

---

## 1. High Concept

You are the master of a Hall that heroes visit with problems. You never leave. You judge the people who arrive, arm them from a small armory of storied items, and give them one piece of advice at the door. Then they walk out, and the story happens without you. A rising Shadow in the east gives every campaign a clock and an ending; the pattern of your advice decides which ending you deserve.

**The one rule:** every mechanic must create stories, not complexity. Anything that does not produce a retellable moment is cut.

---

## 2. Design Pillars

1. **People, not units.** Heroes are assembled from story parts (class, background, virtue and vice, motivation, relationship), never visible stat blocks. The player should think "Elara, the hunter's daughter looking for her father," not "Hero #42, STR 17."
2. **Advice is the weapon.** The signature verb. Equipment and party composition matter, but the final question before every departure is "What do you tell them before they leave?" and the answer changes behavior, not percentages.
3. **The world describes you.** No philosophy picker. The game infers who you are from repeated advice and tells you diegetically, through what people call you.
4. **Failure is content.** Failed missions fail forward: they generate new visitors, worse problems, and grimmer rumours rather than a retry screen.

---

## 3. Core Loop

```
Visitor arrives with a problem
  -> Conversation (judge them: trust, capability, potential)
  -> Preparation (party of up to 3, lend one item)
  -> Advice (choose 1 of 5 stances)
  -> Journey (2 complication events over 2 days, resolved off screen)
  -> Return (triumph / costly / fail-forward / disaster)
  -> Consequence (world state, region health, chronicle entry, surprises)
```

One in-game day is the beat. Each night the Shadow grows, wounded heroes heal, rumours drift in, and active missions advance one event.

---

## 4. Systems

### 4.1 Heroes
Generated from pools: 6 classes (each mapping to one capability: battle, wilds, lore, heart, shadow, words), 18 backgrounds, 8 virtue/vice pairs, 14 motivations, 10 relationships. Heroes track confidence (grows with success), wounds, bonds with other heroes, and a one-line story note. No numeric stats are ever shown.

### 4.2 Advice stances
Cautious, Bold, Diplomatic, Ruthless, Curious. Each mission's complications have a best-fit stance; matching advice grants resolution bonuses and changes event narration. A running tally infers the player's philosophy at 3+ uses of a dominant stance (Compassionate Mentor, Iron Commander, Peacemaker, Opportunist, Scholar), which changes what kind of recruits arrive.

### 4.3 Missions
Template: someone has a problem (20 templates), in a region, against an opposition, needing 1 or 2 capabilities, at a danger level. Fixed beginning, randomized middle (2 of 30 complications), ending determined by party fit, advice, items, bonds, and a die. Four outcome tiers with distinct consequence logic.

### 4.4 World state
Six regions with 0 to 5 health, shown in words (fallen to thriving). Success heals a region, failure and turned-away visitors decay it. Fallen regions accelerate the Shadow.

### 4.5 The Shadow (campaign arc)
Dread 0 to 100, growing nightly, faster per fallen region. Foreshadowed by escalating rumours and three omen scenes with choices (scout / stand steady / research). At 70+ or day 30 the finale unlocks; at 100 it is forced. Finale strength counts confident heroes, settled personal quests, bonds, "dawn" relics, renown, region health, and enemies spared who returned as allies. Four endings: The Dawn Comes, A Hard-Won Dawn, The Long Grey, The Long Night.

### 4.6 Surprise systems
Spared enemies return as recruits. Triumphant parties bring home followers. Confident heroes surface personal quests that resolve their motivations. Bonds form between survivors and matter mechanically and emotionally (grieving on death).

---

## 5. Content Inventory (current build)

20 mission templates, 30 complications, 15 items (3 flagged for the finale), 16 ambient rumours plus 6 Shadow rumours, 8 hall flavor beats, 3 omen scenes, 5 philosophies, 4 endings, 15 SVG scene illustrations, 1 scripted opening (Elara).

---

## 6. UX and Presentation

Single scrolling page in a dark parchment palette. Text unfolds with staggered reveals; choices scroll the reader to the top of each new scene. Canvas ember particles shift mood by ending (gold updraft, grey ash). Dread vignette closes in at screen edges as the Shadow grows. All motion respects `prefers-reduced-motion`. Mobile-first breakpoints below 540px.

**Persistence:** autosave to localStorage after every meaningful action; continue-or-restart on load with a generated "story so far" recap. At campaign end the player can download a styled standalone HTML "bound chronicle" containing achievements, decisions, the fallen, and the full day-by-day record.

---

## 7. Balancing Targets

- Campaign length: 25 to 40 days.
- Mission success rate for a well-matched party with correct advice: about 75 percent.
- A player who ignores the east entirely should reach the finale underprepared but alive.
- Hard rule: no unavoidable hero death in the first 5 days.

---

## 8. Production Roadmap (post-POC)

1. **Content pass:** 60+ mission templates, 100 complications, faction-flavored visitor arcs.
2. **Audio:** ambient hall loop, weather, a leitmotif per philosophy.
3. **Art:** replace SVG scenes with painted stills; hero portraits.
4. **Meta:** cross-campaign Hall legacy (portraits of past campaigns' fallen persist).
5. **Platforms:** itch.io and Steam via wrapper; the single-file architecture ports trivially.

## 9. Risks

Text volume is the production cost center; the engine is cheap. Repetition risk is managed by complication variety and the philosophy system bending content toward the player's identity. Localization multiplies text cost and should be scoped late.
