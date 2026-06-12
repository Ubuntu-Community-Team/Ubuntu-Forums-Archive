---
title: "No sound for totem and xmms..."
date: 2005-09-26
forum: Desktop Environments
---

### Post by YourSurrogateGod on 2005-09-26
Ok, I've tried what was described in [this](http://ubuntuforums.org/showthread.php?t=32063) thread and posted my problem about it [here](http://ubuntuforums.org/showpost.php?p=369170&postcount=85). Now, whenever I try to run xmms and totem side-by-side, there's still no sound, why?

And yes I did everything described in the how-to.

---

### Post by greenstar on 2005-09-26
Open Applications/Sound & Video/Volume Control
then File/Change Device see if the OSS or Alsa device is selected
Alsa didn't work for me, I - like you -  messed around with all sort of complicated stuff trying to get sound to work, to no avail.
Select OSS instead of alsa and see what happens.

greenstar

---

### Post by YourSurrogateGod on 2005-09-26
Well, totem by itself works fine, I'd just like to get it to work in tandem with xmms.

---

### Post by greenstar on 2005-09-26
OK, open XMMS, right-click and select Options/Preferences
then select the Audio I/O Plugins tab and see what is selected for Output Plugin.
Should also be OSS driver.

greenstar

---

### Post by YourSurrogateGod on 2005-09-26
[QUOTE=greenstar]OK, open XMMS, right-click and select Options/Preferences
then select the Audio I/O Plugins tab and see what is selected for Output Plugin.
Should also be OSS driver.

greenstar[/QUOTE]
Thanks, that did the trick :) .

---

### Post by greenstar on 2005-09-26
Glad to help. Those two simple little things stumped me for a while too.;) 

greenstar

---

