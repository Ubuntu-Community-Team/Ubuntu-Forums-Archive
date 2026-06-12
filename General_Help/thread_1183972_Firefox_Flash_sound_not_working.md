---
title: "Firefox Flash sound not working"
date: 2009-06-10
forum: General Help
---

### Post by videomax on 2009-06-10
Hey, when I go to sites like youtube or hulu, instead of hearing the audio, a faint crackling is all that comes out of my speakers. However, I am able to hear mp3s I play juat fine, as well as DVDs.

---

### Post by xngk on 2009-06-10
I had this problem in Hardy and ran
```
sudo apt-get install libflashsupport
```
and restarted Mozilla. I hope that helps.

---

### Post by Hund on 2009-06-10
Have you installed the package "flashplugin-nonfree"? Also make sure you dont have the package "gnash" installed.

---

### Post by videomax on 2009-06-11
Yes and yes. But the sound still doesn't work.

EDIT: I think the problem is with my sound, not with firefox or flash, because when I start my computer it gives the crackling instead of startup sound, and totem is all crackly too. Oddly enough, however, mplayer does sound just fine.

---

### Post by videomax on 2009-06-11
If anyone else has this problem, here is the solution

[http://ubuntuforums.org/showthread.php?t=904677](http://ubuntuforums.org/showthread.php?t=904677)

---

