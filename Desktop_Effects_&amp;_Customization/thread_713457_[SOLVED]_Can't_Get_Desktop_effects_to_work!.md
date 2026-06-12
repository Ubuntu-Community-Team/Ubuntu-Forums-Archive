---
title: "[SOLVED] Can't Get Desktop effects to work!"
date: 2008-03-02
forum: Desktop Effects &amp; Customization
---

### Post by nikRbokR on 2008-03-02
Just installed Gutsy on eternal drive for a laptop on friday.  I have been trying to get a few things working like:
-3D effects
-wireless network connection

Well, regarding 3D effects, I really can't figure out what is wrong.

Here's is my [other post]("http://ubuntuforums.org/showthread.php?p=4440962#post4440962") relating to it.

Help plz!!!!

---

### Post by marufaberlin on 2008-03-03
have you installed compiz-config-settings-manager? (i think that's what its called?)

---

### Post by nikRbokR on 2008-03-05
Well, shouldn't 3D desktop effects (in the menu when you do change background on right-click on desktop) work.  I did the updates it asks you to do after installation.

---

### Post by nikRbokR on 2008-03-23
I installed compiz-config-settings-manager.

Still, I cannot get even the normal desktop effects to work.  Please help!

---

### Post by Ub1476 on 2008-03-23
What's the output of:

```
compiz
lspci | grep VGA
```

---

### Post by nikRbokR on 2008-03-23
well, i figured out that w/ an ATI card, it just wont work, thanks to this [post]("http://ubuntuforums.org/showthread.php?t=722943").

i guess i'll have to figure it out... some other way?

---

