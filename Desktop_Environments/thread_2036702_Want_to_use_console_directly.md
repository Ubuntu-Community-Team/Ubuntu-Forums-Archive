---
title: "Want to use console directly"
date: 2012-08-02
forum: Desktop Environments
---

### Post by leosubhadeep on 2012-08-02
Hi.
Please consider the following:

I use _Unity_,_KDE plasma_, _Gnome 3.x_ and _xfce_ for different user accounts, OS is Ubuntu 12.04 64 bit LTS. From the login screen, I can choose the environment I want to use for every user. Now, my question is: **Can I enter into a console (like konsole or other terminal) *directly* from the lightdm login screen manager**? For example, username "subha-gnome" passsword: "[mypassword]" and environment console (we can do this partially on newer Windows versions by pressing F8 while booting or editing the MBR, but can't choose by default).

I hope I'm clear. Please enlighten me if I can do it and if yes, how.
Thanks in advance.

**Subhadeep**

---

### Post by drmrgd on 2012-08-02
From the login screen if you press Ctrl+Alt+F1 (all the way through F6), you can get a TTY console.  If you want to return to the default TTY running X, you can switch to F7.  Is that what you're looking for?

---

### Post by lukeiamyourfather on 2012-08-02
> **drmrgd said:**
> From the login screen if you press Ctrl+Alt+F1 (all the way through F6), you can get a TTY console.  If you want to return to the default TTY running X, you can switch to F7.  Is that what you're looking for?

To take it a step further you could prevent X and lightdm from ever starting so when booting it simply drops the user to a login prompt.

[http://askubuntu.com/questions/131497/disable-automatic-unity-launching](http://askubuntu.com/questions/131497/disable-automatic-unity-launching)

---

### Post by leosubhadeep on 2012-08-03
> **drmrgd said:**
> From the login screen if you press Ctrl+Alt+F1 (all the way through F6), you can get a TTY console.  If you want to return to the default TTY running X, you can switch to F7.  Is that what you're looking for?

Thanks a ton. **It is EXACTLY what I was looking for**. =D>

---

### Post by leosubhadeep on 2012-08-03
> **lukeiamyourfather said:**
> To take it a step further you could prevent X and lightdm from ever starting so when booting it simply drops the user to a login prompt.

[http://askubuntu.com/questions/131497/disable-automatic-unity-launching](http://askubuntu.com/questions/131497/disable-automatic-unity-launching)

**Thanks to you, too. The post on the link you provided worked. Now I am able to enter even root account, because some shell commands need root access.**

I must say this forum is undoubtedly full of Linux (read Ubuntu) Maestros.


**Subhadeep**

---

