---
title: "Xubuntu: xfce4-panel doesn't autostart"
date: 2007-03-17
forum: Desktop Environments
---

### Post by dhuff on 2007-03-17
Something strange is happening all of the sudden for me with Xubuntu-desktop (installed under 6.06 LTS). 

When I startup the xfce desktop, xfce4-panel doesn't automatically start anymore (tho' I can run it from a cmd line and it'll work). Also, under "Settings Manager," the "Panel" button doesn't do anything anymore.

I don't recall making any deliberate changes to this. Anyone have any ideas ?  :confused:

---

### Post by vialde on 2007-03-20
I have the same problem.  It started after I ran the following code to fix some resolution problems
```
sudo dpkg -reconfigure -phigh xserver-xorg
```

the resolution problems arn't fixed either

---

### Post by twikletoes on 2007-03-21
Type alt + F2 and in the line type xfce4-panel and then you should be able to access your panel options and your panel should work.

---

### Post by maxamillion on 2007-03-21
> **twikletoes said:**
> Type alt + F2 and in the line type xfce4-panel and then you should be able to access your panel options and your panel should work.

Also check the "save session for future logins" when you logout/shutdown/restart to make sure it comes back next time you login

---

### Post by wilberfan on 2007-04-10
I'm having this same problem under the latest Feisty!  :(

Is there some kind of autostart file that could be manually edited, or...?

---

### Post by TinLotus on 2008-06-22
I manually started xfce4-panel through the alt+f2 run dialog.  I have shutdown using applications -> shutdown and I have checked the box for "Save session for future logins" and I have rebooted.  I still do not have xfce4-panel starting at boot, however all my firefox/xterm etc start right back up.

---

### Post by matthew1471 on 2008-07-19
This may help you.

[http://gentoo-wiki.com/Xfce/Installation](http://gentoo-wiki.com/Xfce/Installation)

Look at the section labelled Autostart

---

