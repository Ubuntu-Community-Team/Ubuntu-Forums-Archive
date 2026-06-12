---
title: "xfce4-menueditor segmentation fault and (bad) solution"
date: 2006-06-02
forum: Desktop Environments
---

### Post by AskHL on 2006-06-02
When I start the xfce4-menueditor I immediately receive a segmentation fault error and the program quits. After this has happened, the right-click menu has become completely empty, i.e. the editor has purged the xml file containing the menu data! **Blimey!** :mad: 

Subsequently starting the menu editor will have it working correctly (no segmentation fault), but that damage has been done. My first attempt at solving this was to create a new user (who has the default menu intact!) and retry, and the problem persists (this is actually why I was able to figure out that it was a segmentation fault).

I "fixed" this problem by locating the basic menu.xml file which is at 
```
/etc/xdg/xfce4/desktop/menu.xml
```
and copying this file to
```
~/.config/xfce4/desktop
```
where it overwrote the old now-empty menu.xml, thus restoring the menu to its former glory.

This was quite a waste of time, so I hope this post will save someone else the trouble!! ](*,)

---

### Post by Danielson1218 on 2006-06-02
Thank you, i had the same problem, this fixed it.

---

### Post by ubnoobie on 2006-06-02
a problem with the xfce menu editor is mentioned in the xubuntu release notes: 
[https://wiki.ubuntu.com/XubuntuDapperReleaseNotes#head-b38e122d8c9dc3a3a68b3b1704231a9e90ca7361](https://wiki.ubuntu.com/XubuntuDapperReleaseNotes#head-b38e122d8c9dc3a3a68b3b1704231a9e90ca7361)

---

### Post by IndigoMontoya on 2006-06-02
I had this same problem and instead took a MAJORLY drastic solution...I installed gnome.  lol

---

### Post by sclough on 2006-06-02
I've been trying to figure out why Clicking on the menu did nothing after I launched the menu editor ](*,)

---

