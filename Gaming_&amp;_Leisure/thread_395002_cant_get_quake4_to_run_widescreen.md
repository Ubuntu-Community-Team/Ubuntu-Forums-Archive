---
title: "cant get quake4 to run widescreen"
date: 2007-03-27
forum: Gaming &amp; Leisure
---

### Post by jamesford on 2007-03-27
im unable to make quake run in widescreen mode on my eizo 1680x1050. that means it runs in widescreen but its just stretched 4:3

i googled and changed some things in the config file, like 
seta r_customHeight "1050"

seta r_customWidth "1680"

seta r_fullscreen "1"

seta r_mode "-1"
also made the same changes in console but no help.

any clues?

---

### Post by FoolsGold on 2007-03-27
Close, but you're doing far more work than is necessary.

Download the latest patch first:
[http://www.3dgamers.com/dlselect/games/quake4/quake4-linux-beta-1.4.0.x86.run.html](http://www.3dgamers.com/dlselect/games/quake4/quake4-linux-beta-1.4.0.x86.run.html)

Install, run, then change the aspect ratio option that now appears in the video settings to 16:10 instead of 4:3. This will also provide a new set of resolutions, including 1680x1050, as well as things working with the correct ratio.

If you insist on doing things the hard way (without downloading the patch), all you need to do to fix the aspect ratio problem is to search your config file for the variable

r_aspectRatio

and change it to 2 instead of 0. The rest of your commands are fine, just missing this step.

---

### Post by jamesford on 2007-03-28
thanks man, the new installer did indeed provide me with new resolutions etc, and i can select 16:10 and 1680x1050
i restarted the game, but it still looks like stretched 4:3 to me, because the[ crosshair is oval]("http://img472.imageshack.us/img472/5088/crosshairzm6.jpg") and not round as i guess its supposed to be

dunno if its relevant but ubuntu doesent detect this as a widescreen automaticly, i gotta edit xorg

---

