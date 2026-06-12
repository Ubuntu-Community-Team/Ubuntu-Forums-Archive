---
title: "Hostile takeover by Kubuntu"
date: 2008-07-27
forum: Desktop Environments
---

### Post by Niniel on 2008-07-27
I installed KDE 4 from the repos the other day, just as another WM. Now my boot screen doesn't say Ubuntu anymore, but Kubuntu. That actually looks pretty nice in all its blue glory, but I do find it a bit funny that simply installing another WM can have such... side effects.
Is there an easy way to change it back?

---

### Post by p_quarles on 2008-07-27
This should get you there:
[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)

---

### Post by Niniel on 2008-07-27
Thanks, I'll check it out.
Lol, that guide starts off great though... 
> I do assume that the reader has _basic C programming knowledge_ and knows what a Makefile is for. 
I just want to different boot screen! :)

---

### Post by swisscow on 2008-07-27
try

sudo aptitude install usplash-theme-ubuntu
and then
sudo dpkg-reconfigure usplash

---

### Post by p_quarles on 2008-07-27
> **Niniel said:**
> Thanks, I'll check it out.
Lol, that guide starts off great though... 

I just want to different boot screen! :)
Oops . . . my apologies. Thought that was the link to the how-to change the usplash page, but that's for building your own. 

Here:
[https://help.ubuntu.com/community/USplash](https://help.ubuntu.com/community/USplash)

---

### Post by nikgare on 2008-07-27
KDE is not just a window manager - it's a whole desktop environment!
The wm for kde is, I believe, called kwin.
WHen you instell KDE and all it's cpomponents, you also install kdm, the kde display manager, and the boot screen gets changed.

You could try changing the boot screen with **startupmanager**

---

### Post by Shazaam on 2008-07-27
This might work....
When you get to the login screen go to Sessions (Options?) and choose Gnome instead of KDE.

---

