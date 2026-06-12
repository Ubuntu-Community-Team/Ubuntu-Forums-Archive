---
title: "Configure default window manager"
date: 2009-01-16
forum: Desktop Environments
---

### Post by spinstartshere on 2009-01-16
I recently started using KDE as my main desktop environment as I now find it better than GNOME.  However, I have found that logging in causes Compiz to be used as the window manager, rather than KWin.  Is there a way to change this so that KWin is loaded by default?  I have looked all over the system settings but have not been able to find anythign relevant.  Thanks.

---

### Post by mac71 on 2009-01-16
Hi, have you looked at system settings>default applications and select window manager. From there you can select default (kwin) or another window manager such as compiz or metacity. It should change the setup instantly.

As an after thought, have you tried setting up in the advanced tab of system settings>session manager to run with a empty session (don't know if that'll make a difference):)

---

### Post by spinstartshere on 2009-01-16
I forgot about that...  Correction: I found one thing of relevance, but changing it was only effective until I rebooted.  Thanks for the suggestion, though.

---

### Post by mac71 on 2009-01-18
No problem. Wish I could have been more help. Oh, one thing thats just come to me- have you tried installing fusion icon? run that and switch your window manager from there.

---

### Post by spinstartshere on 2009-01-18
I already have it installed, but I'm one of these people who says that I shouldn't have to do something else in order for it to work properly.

---

### Post by mac71 on 2009-01-18
Yep. I totally understand. It would end up driving me mad too.

---

### Post by benerivo on 2009-01-18
To stop compiz loading on kde startup, i think you can go to the advanced tab in System Settings. Open the autostart section, and disable compiz. This change should be permanent.

---

### Post by spinstartshere on 2009-01-18
It isn't enabled there.

---

### Post by benerivo on 2009-01-18
Check in ~/.kde/autostart and ~/.config/autostart.
Also try disabling desktop effects in gnome (if this is an option).

I forget how the System Settings in kde4 looks, but i remember some option where you choose the default window manager from a drop down list.

---

### Post by txcrackers on 2009-01-18
You could also uninstall Compiz - if you're not using it, why keep it?

---

### Post by spinstartshere on 2009-04-13
I keep it because it's a part of the desktop.  I am still having problems with Compiz loading with KDE4, even when it is disabled in GNOME.  KWin is not showing in the system monitor, only Compiz, whose parent process is ksmserver.  However, I cannot find any mention of Compiz anywhere in the Service Manager or Autostart.

---

