---
title: "Lock Screen = Alt+Ctrl+Backspace?"
date: 2005-08-28
forum: Desktop Environments
---

### Post by Icaros on 2005-08-28
Whenever I do Lock Screen, I get completely logged out just like with Alt+Ctrl+Backspace.  This is particuarly anoying since after x minutes, when my screensaver is supposed to come on and lock the screen, I get totally logged out and all my information is lost.

Help me fix this please!

---

### Post by snpz on 2005-08-29
Ehmm... AFAIK Ctrl+Alt+Backspace restarts X server. Ctrl+Alt+L maybe locks screen? Really don't remember!

---

### Post by hashimoto on 2005-08-29
I think that s/he says the effect of 
"Ctrl+Alt+L" (or whatever) = Ctrl+Alt+Backspace
That is: trying to lock the screen kills X and restarts it.

Dunno. Somebody else?

---

### Post by bonedaddy659 on 2007-08-25
This is the same problem I'm having when my system is idle for too long it goes to the login screen once I login again it effectively kills the x server and all my stuff I was working on is lost I'm running 7.04 and have the restart the xserver with each login unchecked any ideas. Thanks

---

### Post by Wolki on 2007-08-25
Does it always happen immediately after locking the screen? If not, it might have to do with a buggy screensaver; try using the blank screensaver theme and see if it works then.

---

### Post by mcduck on 2007-08-26
Do you have a decent graphics card and proper drivers for that? If not, 3D screensavers can cause behavior like that. Try using only one, simple screensaver that you know not to crash your desktop.

---

### Post by kdx on 2007-09-04
I'm having the same problem, only mine randomly restarts/crashes X.  Sometimes it happens when I allow the screensaver to come on automatically, others it happens when I manually lock the screen.  Either way, it's only sporadically and it's a bit annoying.  

I have an ATI graphics card and I'm running Feisty with Compiz Fusion, but I had this issue before I installed Fusion.

I'll try the blank screensaver (I'm currently using Flurry that comes with Feisty).  

Any other ideas?

Edit:  
I was previewing screensavers and clicking the "next" arrow when suddenly X restarted.  I went back to see which screensaver caused the crash, and it turned out to be a 3D 'saver.  

I guess I can also add some more information about my system.  I have a Dell Inspiron E1505 and I'm using Gnome, although I do run some KDE apps as well, such as Amarok and Koctave.

---

### Post by Wolki on 2007-09-04
> **kdx said:**
>  
I was previewing screensavers and clicking the "next" arrow when suddenly X restarted.  I went back to see which screensaver caused the crash, and it turned out to be a 3D 'saver.  

I guess I can also add some more information about my system.  I have a Dell Inspiron E1505 and I'm using Gnome, although I do run some KDE apps as well, such as Amarok and Koctave.

Running KDE stuff shouldn't matter. It's probably an incompatibility between the 3D screensavers, your computer, and compiz. Try filing a bug in Launchpad or Gnome Bugzilla, preferrably with the screensaver's name included.

It'd also be interesting to know which graphics card and driver you use. Iy you're running compiz with ATI, does that mean you're using XGL? I remember that introducing extra compatibility problems with 3d applications, but I'm not sure as I don't know much about composited bling.

---

### Post by kdx on 2007-09-10
> **Wolki said:**
> Running KDE stuff shouldn't matter. It's probably an incompatibility between the 3D screensavers, your computer, and compiz. Try filing a bug in Launchpad or Gnome Bugzilla, preferrably with the screensaver's name included.

It'd also be interesting to know which graphics card and driver you use. Iy you're running compiz with ATI, does that mean you're using XGL? I remember that introducing extra compatibility problems with 3d applications, but I'm not sure as I don't know much about composited bling.

Yeah, I'm using Gnome + XGL to get it to work.  My graphics card is a 128MB ATI MOBILITY RADEON X1300 HyperMemory (from my order detail from Dell).

---

### Post by ubuntukerala1980 on 2007-09-10
In gnome lock screen is Alt+ctrl+l
:guitar:
It works perfectly for me :guitar:

---

### Post by ubuntukerala1980 on 2007-09-10
If you are using gnome 
System -> Preferences -> Keyboard Shortcuts 
Now check key for lock screen
:lolflag:

---

### Post by kdx on 2007-09-11
> **Icaros said:**
> Whenever I do Lock Screen, I get completely logged out just like with Alt+Ctrl+Backspace.  This is particuarly anoying since after x minutes, when my screensaver is supposed to come on and lock the screen, I get totally logged out and all my information is lost.

Help me fix this please!

I think some of you are misunderstanding what this post is saying.  He is saying that both when he locks his screen, as well as when the screensaver comes up, it behaves as if he hit Ctrl + Alt + Backspace...not that he's hitting Ctrl + Alt + Backspace to lock it.

I am having the same problem, and I guarantee you that I understand the difference between the two.

---

### Post by ilektron on 2007-09-13
I'm having a similar problem with XGL, fglrx and Compiz Fusion.  My problem is that I can do it once in a while but when I usually try locking my computer freezes, and I have to do a hard reset. (Using alt-sysrq)  Also, logging out has the same problem.  I wonder if this has something to do with the startxgl options...

---

