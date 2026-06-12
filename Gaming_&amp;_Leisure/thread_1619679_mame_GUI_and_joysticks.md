---
title: "mame GUI and joysticks"
date: 2010-11-12
forum: Gaming &amp; Leisure
---

### Post by rupert on 2010-11-12
Hi,

i have an arcade Controller working on my ubuntu box and would like to know
which mame GUI does support menu browsing with the arcade controller?

I tested gmameui and it only works partiall, i can only browse the list up not down, also starting games from the gui doesnt work.

I also tried wahcade, but this doesnt let me start a game at all.
I think this is because mame doesnt work on the commandline, so gmameui does something
wahcade doesnt.


MY Controller is a Madcatz fightstick from the xbox360.


thnx

---

### Post by rupert on 2010-11-12
well i nailed it down to sdlmame, it seems gmameui does use its own config settings which are better than the ones in the default mame.ini.
Is there a way to even these 2 up?

---

