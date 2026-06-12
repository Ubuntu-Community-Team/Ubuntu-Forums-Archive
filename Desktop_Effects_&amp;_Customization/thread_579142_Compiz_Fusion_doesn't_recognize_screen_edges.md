---
title: "Compiz Fusion doesn't recognize screen edges"
date: 2007-10-18
forum: Desktop Effects &amp; Customization
---

### Post by King_Critter on 2007-10-18
Compiz Fusion is doing this really weird thing... See, I've got a gnome-panel set to auto hide on the left side of my screen. I edited some stuff in GConf to get it to hide all the way (0 pixels). While using Metacity everything's fine and dandy; but when I start up Compiz Fusion and move my mouse over to the screen edge... nothing. After some experimentation, I found that Compiz seems to have a "dead zone" where it doesn't register movement or clicks about 2 pixels wide. A tempororary solution, of course, is just to change the panel hide settings to 3 pixels -- which I've done. But I would like my completly invisible panels back, so if anyone can help...?

---

### Post by Forlong on 2007-10-18
Do you use the wall plugin (default in Gutsy)?
I remember having a similar issue with that.
Try switching to the cube and if it works, consider filing a bugreport.

---

### Post by gregbzh on 2007-10-18
I'm having a similar problem when I have the cube enabled in Gutsy.  I have that same "dead zone" when I try to open the Firefox all-in-one sidebar.  The sidebar works fine when the cube is disabled.

---

### Post by King_Critter on 2007-10-18
Yup, it was the cube... which kinda sucks, 'cause I like the cube. :-/ 

Oh well, I hope they fix that soon. Thanks to both of 'ya!

---

### Post by Forlong on 2007-10-19
Please file a bugreport (or look for an existing one and see if you can add something).
It won't just fix itself.

---

### Post by gregbzh on 2007-10-19
No worries mate.  I'll do just that as soon as I work out how to file a bug report.:confused:

---

### Post by Forlong on 2007-10-19
> **gregbzh said:**
> No worries mate.  I'll do just that as soon as I work out how to file a bug report.:confused:
Oh, that's quite easy: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) :)

---

### Post by gregbzh on 2007-10-19
Thanks.  I'll give it a try this evening.

---

### Post by 23meg on 2007-10-20
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/103306](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/103306)

---

