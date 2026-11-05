# Kanxiang (Physiognomy Skill)
> *"Appearance reflects the heart, destiny is shaped by oneself. Facial features, palm lines, bone structure, and body form are all manifestations of life's trajectory."*

**Ancient wisdom of physiognomy, reflecting millennia of insight**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Skill-blueviolet)](https://claude.ai/code)
[![AgentSkills](https://img.shields.io/badge/AgentSkills-Standard-green)](https://agentskills.io)

**Language**：[English](README_EN.md) | [简体中文](README.md)

This repository focuses on human physiognomy through the `tenpai-kanxiang` skill, covering face, palm, bone, and body reading based on traditional Chinese physiognomy.

⚠️ **This analysis is for cultural reference and entertainment only. Modern science has not reached a consensus on the predictive ability of physiognomy.**

[Features](#features) · [Examples](#examples) · [Knowledge Sources](#knowledge-sources) · [Important Notes](#important-notes)

---

## Installation

Install the human physiognomy skill with the [skills CLI](https://skills.sh) (`npx skills`):

```bash
# Install the repository skill to the current project
npx skills add tenpai-ai/kanxiang

# Target a specific agent
npx skills add tenpai-ai/kanxiang --skill tenpai-kanxiang -a opencode
```

Notes:
- At the install prompt choose **Symlink** so skills stay in sync with the repo, or **Copy** for independent copies
- The repo must be pushed to GitHub and public; before that, install from a local path instead: `npx skills add /path/to/kanxiang`
- Management commands: `npx skills list` to view, `npx skills update` to update, `npx skills remove <skill-name>` to uninstall
- If you installed the previous `human-physiognomy` name, run `npx skills remove human-physiognomy` in the same scope, then install `tenpai-kanxiang`

### Skills in This Repository

| Skill | Purpose | Input | Output |
|-------|---------|-------|--------|
| [`tenpai-kanxiang`](skills/tenpai-kanxiang/SKILL.md) | Human readings: confirm the photo and type first; face, palm, bone and body reading as requested, per classic texts such as 《麻衣神相》 and 《冰鉴》 | Face / palm / bone / full-body photos | Conversational reading in the “老夫” voice; annotated original when the image tool supports it |

---

## Usage

### Basic Usage

1. **Upload a photo and specify the type**:
   ```
   Read my face [upload face photo]
   ```

2. **Or upload a photo by itself**: when the photo clearly shows one type, the skill selects the matching rules automatically. If the type is unclear, multiple types are possible, or the photo conflicts with your request, it asks you to confirm first.

3. **If you have no photo**: the skill asks you to upload one. If you have not chosen a reading type, it lists face, palm, bone, and body reading, asks you to choose, and requests a matching photo.

The skill confirms the photo and type before reading any rules. If the current environment has a tool that can annotate the original image, it produces a copy with callout lines; otherwise, it gives a conversational reading in the “老夫” voice and names its sources.

### Supported Analysis Types (tenpai-kanxiang)

| Type | Description | Photo Requirements |
|------|-------------|-------------------|
| **Face Reading** | Analyze features, three courts, twelve palaces, complexion | Front face photo preferred; a side profile only supports visible contours |
| **Palmistry** | Analyze palm lines, finger shapes, mounts, coloration | Palm front photo |
| **Bone Reading** | Analyze skull, body bones, nine bone structures | Photo showing bone contours |
| **Body Physiognomy** | Analyze body type, posture, temperament | Full-body or half-body photo |

---

## Examples

### Example 1: Photo present, type clear (face reading)

> Input: `Read my face [upload face photo]`

```
User ❯ Read my face
[Upload face photo]

Kanxiang Skill ❯ Let this old fellow take a look. In this photo the forehead looks fairly open, and the brow ridge is easy to see.

In traditional face reading, the upper court is often discussed in terms of early foundations and thinking, while the brow ridge is often linked to temperament and decisiveness. I will stick to the features that are clearest in the photo and not overstate them. With those details out of the way, the overall impression is fairly steady and composed, and the gaze does not look especially sharp; in the old idiom, this suggests someone who acts with measure and does not rush in. The relevant rules are compiled from traditional face-reading material such as 《麻衣神相》.

(When the current environment has a tool that can edit the original image, an annotated copy is attached here, with callout lines pointing to the forehead, brow ridge and other analysed areas. Each label has the area name on the first line and a brief visible description on the second, such as “Forehead / fairly open and full” or “Brow ridge / slightly prominent”. For an English question, the labels are in English too. Without such a tool, only the text reading is given, with a note that no annotated image could be produced.)
```

### Example 2: No photo and no reading type

> Input: `Read my physiognomy`

```
User ❯ Read my physiognomy

Kanxiang Skill ❯ I can read the face, palm, bone structure, or body form. Which one would you like? Choose one and send a matching photo: a face, a palm, a photo showing bone contours, or a full-body or half-body shot.
```

### Example 3: Text and photo do not match

> Input: `Read my body form [upload palm photo]`

```
User ❯ Read my body form
[Upload palm photo]

Kanxiang Skill ❯ Hmm, what I see here is a palm. Would you like to switch to palm reading, or keep the body reading and add a full-body or half-body photo?
```

### Example 4: Photo is unclear

> Input: `Take a look [upload blurry photo]`

```
User ❯ Take a look
[Upload blurry photo]

Kanxiang Skill ❯ This photo is too unclear for me to read properly. Were you after face, palm, bone, or body reading? If convenient, send a clearer matching photo and I will take a closer look.
```

---

## Features

### Supported Physiognomy Types

| Type | Analysis Dimensions | Source Materials |
|------|-------------------|------------------|
| **Face Reading** | Features, three courts, twelve palaces, complexion | "Mayi Shenxiang", "Lizhuang Xiangfa", "Shenxiang Quanbian" |
| **Palmistry** | Palm lines, finger shapes, mounts, coloration, patterns | "Shenxiang Quanbian", "Shuijing Shenxiang" |
| **Bone Reading** | Skull, body bones, nine bone structures | "Taiqing Shenjian", "Renlu Datong Fu" |
| **Body Physiognomy** | Body type, posture, temperament, gait | "Bingjian", "Shenxiang Quanbian" |

### Output Style

- **Reply language follows the question**: answer in Chinese when asked in Chinese, in English when asked in English; if the user explicitly requests another language, use that one. Confirmations, readings, fallback notes, and image labels all use that language. In English replies, use common English terms for body areas and palaces, with the Chinese name in parentheses when useful.
- **Details first, overall last**: discuss specific areas and visible features first, then close with the overall impression and personality; do not lead with a verdict about the person. Image labels carry only concrete visible features; overall judgments and personality stay in the closing text.
- **“老夫” voice**: speaks as “this old fellow”, in a warm, conversational tone, with an occasional “hmm” or “ah”.
- **On demand**: explains the areas and questions the user asks about, without mechanically filling a fixed report template.
- **Sources**: major observations name the reference text; only book-level attribution supported by the knowledge base is given, with no invented chapters, pages, or quotations.
- **Annotated original**: when the current environment has an image-editing tool that can work from the user's original photo, it produces an annotated copy that preserves the person's appearance and uses callout lines to mark the analysed areas. Each label has two lines: the area name on top and a brief visible description below (e.g. “Mouth Palace / lips on the thin side”, “Forehead / fairly open and full”). Without a suitable tool, it gives a text reading and says so.

### Technical Principle

```
Check photo → Confirm type when needed → Read rules → Analyse visible features
            → Try original-image annotation → Deliver annotated image or text reading
```

1. **Check photo**: if no usable photo is present, ask for one; if no reading type is stated, list the four types for the user to choose.
2. **Confirm type**: proceed directly when the photo is clear and matches the request; ask first when the type is unclear, several parts are present, or the photo conflicts with the text.
3. **Read rules**: after confirmation, read the matching face, palm, bone, or body rule file.
4. **Analyse features**: discuss only clearly visible areas and separate visible features from traditional interpretations.
5. **Deliver**: attach an annotated original when an image-editing tool is available; otherwise give a conversational text reading.

---

## Knowledge Sources

This skill's rule knowledge base is compiled from the following classic physiognomy texts:

| Classic | Author/Dynasty | Main Content |
|---------|----------------|--------------|
| **"Mayi Shenxiang" (麻衣神相)** | Mayi Taoist (Northern Song) | Foundational work of face reading, systematic face reading theory |
| **"Lizhuang Xiangfa" (柳庄相法)** | Yuan Yong (Early Ming) | Rich practical cases, focused on practical application |
| **"Shenxiang Quanbian" (神相全编)** | Yuan Zhongche (Ming Dynasty) | Comprehensive collection of physiognomy, covering face, palm, and bone reading |
| **"Shuijing Shenxiang" (水镜神相)** | Fan Li (attributed) | Concise and practical, suitable for beginners |
| **"Bingjian" (冰鉴)** | Zeng Guofan (Qing Dynasty) | Person observation art, focused on temperament and talent |
| **"Taiqing Shenjian" (太清神鉴)** | Anonymous (Song Dynasty) | Bone structure and complexion, integrating form and spirit |
| **"Renlu Datong Fu" (人伦大统赋)** | Anonymous (Jin-Yuan Dynasty) | Verse-style physiognomy, facilitating memory and transmission |

---

## Project Structure

The skill directory follows the [AgentSkills](https://agentskills.io) open standard:

```
kanxiang/                         # Human physiognomy skill repository
├── skills/
│   └── tenpai-kanxiang/          # Human physiognomy skill
│       ├── SKILL.md              # Skill entry (official frontmatter)
│       └── references/           # Rule knowledge base
│           ├── mianxiang.md      # Face reading rules (based on "Mayi Shenxiang", etc.)
│           ├── shouxiang.md      # Palmistry rules (based on "Shenxiang Quanbian", etc.)
│           ├── guxiang.md        # Bone reading rules (based on "Taiqing Shenjian", etc.)
│           └── tixiang.md        # Body physiognomy rules (based on "Bingjian", etc.)
├── README.md                     # This file
└── LICENSE
```

---

## Important Notes

### ⚠️ Important Reminders

- **This analysis is for cultural reference and entertainment only**: Physiognomy is traditional culture; modern science has not confirmed its predictive ability
- **Please view rationally**: Life path depends primarily on personal effort and choices
- **No absolute assertions**: All analyses are probabilistic references, not absolute destiny
- **No medical judgments**: Skin tone, palm lines, or bone features must not be used for diagnosis; consult a professional doctor for health concerns

### 📋 Usage Limitations

- No prediction of specific events or dates (e.g., "when will I get married", "when will I get rich")
- No politically sensitive topics
- No promotion of superstition
- Outputs retain a cultural-reference note and do not present physiognomy as a scientific conclusion

### 📷 Photo Requirements

- **Clarity**: Photos should be clear and visible, avoid blur or obstruction
- **Lighting**: Avoid overly dim lighting or direct strong light
- **Angle**: A front view is best; a side profile is only used for the contours visible from that angle
- **Privacy**: Do not upload photos containing others' privacy

---

## FAQ

### Q: Is the analysis accurate?
**A**: Physiognomy is part of traditional culture and can be used as a reference, but should not be superstitious. Modern science has not reached a consensus on the predictive ability of physiognomy. It is recommended to treat analysis results as entertainment and cultural reference, and view them rationally.

### Q: What types of photos can I upload?
**A**: Supports human body part photos, including face, palm, full body, etc. Photos should be clear and visible, avoiding blur, obstruction, overly dim lighting, etc.

### Q: How long does analysis take?
**A**: Typically completed within a few seconds to a few dozen seconds.

### Q: Can I upload photos for analysis multiple times?
**A**: Yes. Each analysis is independent, and you can upload different photos for analysis multiple times.

### Q: Will analysis results be saved?
**A**: No. Each analysis is real-time and does not save your photos or analysis results.

### Q: What physiognomy types are supported?
**A**: Currently supports four major categories: face reading, palmistry, bone reading, and body physiognomy. More types may be added in the future.

---

## Version History

### v1.1.2 (2026-11-05)
- Reading order now starts with specific areas and features, then closes with overall impression and personality
- Image annotations mark concrete features only; overall judgments stay in the closing text

### v1.1.1 (2026-11-05)
- Replies and image labels follow the language of the user's question
- Image labels now use two lines — area name on top, brief visible description below — instead of the name alone

### v1.1.0 (2026-11-05)
- Renamed the skill to `tenpai-kanxiang`
- Confirm the photo and reading type first; ask when no photo, an unclear type, or a photo/text mismatch
- Conversational “老夫” delivery; annotated original when an image tool supports it, otherwise a text reading
- Book-level source attribution only, with no invented chapters, pages, or quotations

### v1.0.0 (2026-04-19)
- Initial release
- Supports four major analysis categories: face, palm, bone, body
- Rule knowledge base compiled from seven classic physiognomy texts
- Complete analysis report structure
- Automatic photo type recognition

---

## Concluding Thoughts

Physiognomy is the crystallization of ancient wisdom in observing humans and nature.

It is not superstition, but a systematic summary of experience. From face reading to personality, palmistry to tendencies, bone reading to life patterns, body physiognomy to temperament—these are our ancestors' ways of understanding the complex system that is "human".

Of course, modern science tells us that destiny is never written on appearance.

Your personality, abilities, and fortune depend more on your choices, efforts, and encounters. Physiognomy analysis can serve as an interesting reference, a window to understand the charm of traditional culture, but it is never a life compass.

True "appearance transformation" lies not in external decoration, but in inner cultivation.

As "Bingjian" says: "The spirit of the whole body is embodied in the two eyes; the bone structure of the whole body is revealed in the face." Spirit and temperament are the ultimate pursuit of physiognomy.

---

MIT License © [timerzz](https://github.com/tenpai-ai/kanxiang)

**Last Updated**: 2026-11-05
**Skill Version**: 1.1.2
