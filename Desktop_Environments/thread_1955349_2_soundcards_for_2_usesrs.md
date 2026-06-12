---
title: "2 soundcards for 2 usesrs"
date: 2012-04-09
forum: Desktop Environments
---

### Post by Fisher on 2012-04-09
Hi.
I am using a Ubuntu multiseat configuration for years and it was working fine. This allows me to use a single PC for 2 users, with 2 different mices, keyboards, monitors, video and sound cards.
Since I upgraded to 10.04, I started having sound card problems, both users are getting the sound output on the same sound card, totally ignoring the settings.
In the beginning, it was just a matter of restart the system and BANG! Everything was working as it should! But now, this solution doesn't work so easily, normally needing up to 10 restarts!!
Is there a way I can fix it? If I change one user's default hardware output on one seat it gets changed on the other too. I'm using sound preferences to do it, is there any other place I can do this setting? How can I do a per user setting? The old ~/.asoundrc doesn't seem to work anymore.
Please, help!!

---

### Post by Fisher on 2012-04-11
Found a solution!!
I just used padevchooser and selected the default sink for the desired sound card.
My only doubt is: Will it be working after the next reboot?
Well, if not I'll post here again!!

---

