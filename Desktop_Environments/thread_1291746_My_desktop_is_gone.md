---
title: "My desktop is gone"
date: 2009-10-15
forum: Desktop Environments
---

### Post by xjsquarred on 2009-10-15
Hi, I have UNR 9.04 on a dell mini 12.  The UNR desktop was making my netbook run slowly.  For a while I simply switched to the classic ubuntu desktop every time I started the computer.  Then I opened startup options and de-selected the UNR desktop, figuring it would revert to the classic desktop.  Now my computer starts and shows the background image and desktop icons only.  I am able to open nautilus and browse the files.  I can click "get help online" to open firefox.  I tried searching for similar problems or quick keys that could open the settings to correct the problem, but I haven't found anything.  Thanks in advance...
Reed

---

### Post by wilee-nilee on 2009-10-15
> **xjsquarred said:**
> Hi, I have UNR 9.04 on a dell mini 12.  The UNR desktop was making my netbook run slowly.  For a while I simply switched to the classic ubuntu desktop every time I started the computer.  Then I opened startup options and de-selected the UNR desktop, figuring it would revert to the classic desktop.  Now my computer starts and shows the background image and desktop icons only.  I am able to open nautilus and browse the files.  I can click "get help online" to open firefox.  I tried searching for similar problems or quick keys that could open the settings to correct the problem, but I haven't found anything.  Thanks in advance...
Reed

So a quick look with Google shows some problems in general with the dell mini's in general hopefully you can get some help on the forums but you may look at the web.

---

### Post by ugm6hr on 2009-10-16
What did you want to do?  Go to the standard Gnome desktop, or the nebook remix?

---

### Post by xjsquarred on 2009-10-18
either would be fine, right now i have no desktop.  Preferably the classic desktop.

---

### Post by ugm6hr on 2009-10-18
Press Alt+F2: gnome-terminal

In the terminal:
```
sudo apt-get remove netbook-launcher maximus
```

Reboot, and see if it is solved.

If not, install reset gnome again:
In nautilus, show hidden files in /home/username
Delete all the .gnome and .gconf and .nautilus folders

Reboot

---

