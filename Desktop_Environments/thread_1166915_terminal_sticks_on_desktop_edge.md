---
title: "terminal sticks on desktop edge"
date: 2009-05-22
forum: Desktop Environments
---

### Post by salakhate on 2009-05-22
Hi all,
My graphics card is a bit old and the terminal sometimes shakes when I move it around the desktop. But when I move any terminal/window to the corner of desktop, the terminal/window gets stuck there and have to move my mouse a lot to pull it. It is really annoying.

Can anyone help me with how I can disable this pulling effect?

Thanks in advance!

---

### Post by gettinoriginal on 2009-05-22
You do not say if you are using compiz or not, but it sounds to me as if you have a window setting causing this.  If you are using compiz, you could go into CCSM and check your settings, or you can copy/paste into terminal:
```
gconftool-2 --recursive-unset -a /apps/compiz
```  This sets compiz back to default settings.

---

### Post by Kevbert on 2009-05-22
It sounds like you're using compiz-fusion (the cube) and have got Wobbly Windows and Snapping Windows enabled. If you run up the Compiz Settings Manager, Wobbly Windows is under Effects and Snapping Windows is under Window Management. Make sure both boxes are unticked.

---

### Post by salakhate on 2009-05-23
Thanks a lot.
Tried it and i think it set all settings to default.
I like the wobbly windows but if i enable that, i still have the problem. Any idea to use wobbly windows effect without having such sticking effect? 
I am using compiz.

Thanks again!



> **gettinoriginal said:**
> You do not say if you are using compiz or not, but it sounds to me as if you have a window setting causing this.  If you are using compiz, you could go into CCSM and check your settings, or you can copy/paste into terminal:
```
gconftool-2 --recursive-unset -a /apps/compiz
```  This sets compiz back to default settings.

---

### Post by salakhate on 2009-05-23
Hi,
Thanks a lot.
It solved my problem.
I let the wobbly windows checked and just unchecked the snapping windows.




> **Kevbert said:**
> It sounds like you're using compiz-fusion (the cube) and have got Wobbly Windows and Snapping Windows enabled. If you run up the Compiz Settings Manager, Wobbly Windows is under Effects and Snapping Windows is under Window Management. Make sure both boxes are unticked.

---

### Post by gettinoriginal on 2009-05-24
Glad you got it straightened out.  Enjoy  :p

---

