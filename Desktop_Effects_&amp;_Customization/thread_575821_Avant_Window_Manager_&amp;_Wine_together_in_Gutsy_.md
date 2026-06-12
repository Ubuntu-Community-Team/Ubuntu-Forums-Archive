---
title: "Avant Window Manager &amp; Wine together in Gutsy -- SUPER SLOW"
date: 2007-10-14
forum: Desktop Effects &amp; Customization
---

### Post by EnigMattic on 2007-10-14
Hi

I am using AWN & Wine on the latest Gutsy pre-release.
Everything is fine UNLESS I launch anything with Wine (eg Dreamweaver or DVDShrink), at which point the entire system becomes unusably  slow until either AWN or the Wine app is shutdown.

I just don't get it. I use a lot of combinations of processor-intensive tasks and this seems to be the only one that generates any problems at all.

Any advice would be greatly appreciated!!!

I did find [THIS]("https://bugs.launchpad.net/awn/+bug/151317"), but I don't want to risk messing up my whole system by altering settings I don't understand in xorg.conf.

---

Slightly OT, does anyone know how to get AWN to use Openoffice launchers to represent the appropriate tasks, rather than creating a seperate icon? Does anyone know how to change the spacing of icons?
[B]
CHEERS![/B]

---

### Post by Faud on 2007-10-14
I would try running compiz-fusion with indirect rendering "yes" before I did anything else to be honest. Then if that doesnt help then just change it back to "no"
usr/bin/compiz
Open it with a text editior (you may need to be root to save it) then just change the line from no to yes for indirect rendering.

---

### Post by EnigMattic on 2007-10-14
Thank you! :)
That did the trick!
YOU ROCK :guitar:

> **Faud said:**
> I would try running compiz-fusion with indirect rendering "yes" before I did anything else to be honest. Then if that doesnt help then just change it back to "no"
usr/bin/compiz
Open it with a text editior (you may need to be root to save it) then just change the line from no to yes for indirect rendering.

---

### Post by EnigMattic on 2007-10-23
UPDATE:
Since reformatting and installing the full release of Gutsy, I now get the following error if I apply this fix:

```
Internal Error
failed to initialize HAL!
``` :confused:
Any more ideas? Anyone?

---

### Post by Goronok on 2007-10-25
> **Faud said:**
> I would try running compiz-fusion with indirect rendering "yes" before I did anything else to be honest. Then if that doesnt help then just change it back to "no"
usr/bin/compiz
Open it with a text editior (you may need to be root to save it) then just change the line from no to yes for indirect rendering.

I have the same problem with Wine & AWN not working well together.  With both running at the same time, my whole machine freezes for a brief second VERY often. (When I say freeze, screen is completely locked.. even the mouse stops moving)  I tried editing the compiz file for indirect rendering and that didn't seem to do anything to help the situation.   Anyone have any other ideas and/or suggestions?

---

### Post by LavianoTS386 on 2007-10-25
In WINE conf. go to Desktop Intergration and deselect the checkbox that mentions the window manager.

---

### Post by asgard_command on 2007-12-11
I don't know if there is any connection. I don't have a problem with slow down running wine and awm. 

My problem is trying to add a launcher to AWM for a program running in wine.
I can add the launcher and it seems fine but once it disappeared other times it just seems to stop working.

---

