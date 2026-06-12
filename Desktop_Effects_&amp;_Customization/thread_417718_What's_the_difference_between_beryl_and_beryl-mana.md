---
title: "What's the difference between beryl and beryl-manager?"
date: 2007-04-21
forum: Desktop Effects &amp; Customization
---

### Post by vtian on 2007-04-21
I installed beryl on Feisty 2 days ago, it works perfect. However, this morning after booting, the beryl effect is gone...  There is nothing happened after run **beryl-manager**. I tried to run **beryl** instead of beryl-manager, it works. but the window frame lost.  

The /etc/X11/xorg.conf is correct, 

Option          "AddARGBGLXVisuals"     "True" 
Defaultdepth    24

I tried to fix the window frame with 
**metacity --replace**
The window frame comes back, but I get back to the original gnome desktop with no beryl effects at all.

What's the problems? Any ideas?

---

### Post by blitzer on 2007-04-21
I think I get what your saying, do you have the Beryl icon on the task bar ?  Just right click on it and go to Select Window Manager and select Beryl or Compiz.  The effects should be back.

If the Icon is not there it will be under Applications > System tools >Beryl Manager.

---

### Post by vtian on 2007-04-21
Thanks blizer, it works perfect.:) 

> **blitzer said:**
> I think I get what your saying, do you have the Beryl icon on the task bar ?  Just right click on it and go to Select Window Manager and select Beryl or Compiz.  The effects should be back.

If the Icon is not there it will be under Applications > System tools >Beryl Manager.

---

### Post by blitzer on 2007-04-21
Excellent :guitar:   Happy Ubuntuing.

---

