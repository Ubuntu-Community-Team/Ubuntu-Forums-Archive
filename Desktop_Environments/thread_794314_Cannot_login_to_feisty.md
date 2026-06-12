---
title: "Cannot login to feisty"
date: 2008-05-14
forum: Desktop Environments
---

### Post by wayneh on 2008-05-14
I upgraded to feisty 5 months ago and yesterday my logins failed. All 5 users on that box fail to login to gnome and kde. The username/password screen is displayed, I pick and user and enter the corresponding password and hit Enter. I see a black screen for a few seconds, then the login screen is returned with no error messages displayed. 

The default on that box is KUBUNTU; and picking either GNONE or KDE both fail. I do have automatic enabled updates on that box so maybe some new update has caused this? 

I do not know how to bypass this, or how to fix it. Any suggestions?

Correction; I upgraded from feisty to gutsy 5 months ago.

---

### Post by macaholic on 2008-05-14
What kind of graphics card do you have?

---

### Post by NightwishFan on 2008-05-14
Perhaps do a ctrl+alt+f1 and log in there. Then type:
```
startx
```

---

### Post by Xiong Chiamiov on 2008-05-15
I believe that's been an issue for some.  Aside from the graphics card, are you using the proprietary driver?  What about if you do a
```

sudo dpkg-reconfigure -phigh xserver-xorg

```
(but back up your current xorg first!:
```

cd /etc/X11
sudo cp xorg.conf xorg.conf.bak20080514

```)

---

