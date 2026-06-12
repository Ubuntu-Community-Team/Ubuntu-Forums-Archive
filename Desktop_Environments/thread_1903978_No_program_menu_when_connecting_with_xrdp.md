---
title: "No program menu when connecting with xrdp"
date: 2012-01-03
forum: Desktop Environments
---

### Post by ctyonahl on 2012-01-03
I installed xrdp to connect to my Ubuntu machine from my Windows 7 machine. Logging in is easy, but no menus appear. Open windows display fine, but there is no way to launch a program, etc. Here's a screenshot of what I'm seeing: 

[IMG]http://dl.dropbox.com/u/33761344/Capture.PNG[/IMG]

Anybody know why this is happening?

---

### Post by josephmills on 2012-01-03
what happenes when you right click the desktop ?or alt+f2 ?

---

### Post by ctyonahl on 2012-01-03
> **josephmills said:**
> what happenes when you right click the desktop ?or alt+f2 ?

Nothing....

---

### Post by ctyonahl on 2012-01-05
*bump* still nothing on the screen.

---

### Post by ctyonahl on 2012-01-18
Well, this sure has been a meaningful discussion.... :-k

---

### Post by Xfool on 2012-03-30
duncang92's xrdp solution worked for me.
[http://ubuntuforums.org/showpost.php?p=11683215&postcount=8](http://ubuntuforums.org/showpost.php?p=11683215&postcount=8)

---

### Post by AOINEKO on 2012-10-22
It doesn't work in ubuntu 12.10, ubuntu-2d is deprecated, you can use:

"gnome-session --session=gnome-fallback" in ~/.xsession


echo "gnome-session --session=gnome-fallback" > ~/.xsession

---

