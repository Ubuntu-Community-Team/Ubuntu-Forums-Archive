---
title: "Font rendering and african and vietnamese languages"
date: 2005-05-12
forum: Desktop Environments
---

### Post by andj_c on 2005-05-12
Hi all,

I've just installed Ubuntu and am evealuating it for my needs. Currnetly i'm working with a range of Vietnamese Ethnic Minority languages and languages form East and West Africa.

I've managed to write and install some xkb layouts for some of these languages and can now type in them.

My next task is to try to get the text displaying correctly. They use the Latin script and require correct placement of combining diacritics above and below base characters and handle diacritic staking.

i.e. these are languages that have character requirements where this is necessary, that is, there are no precomposed unicode characters available.

My question, is there any way to get the font rendering system to use OpenType fonts using GSUB and GPOS tables for Latin script?

Currently, even when using appropariate OpenType fonts, some oddities occur within the display, overstriking capital letters, overstriking diacritics, and visual placement of diacritics on the letter before the base character.

Or is this something i need to discuss with the pango people?

Andj

---

