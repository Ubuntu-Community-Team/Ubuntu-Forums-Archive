---
title: "Can you use nvidia driver with evilwm/server install?"
date: 2007-06-20
forum: Desktop Environments
---

### Post by jseiser on 2007-06-20
I have failed in being able to do so, I cant even do it on the xubuntu-desktop i installed because it says i need a linux-restricted-modules-version-server.  i cant find a "server" version. I tried installing Generic and that failed as well.  How would one go about installing the driver from the cli??\



edit: if i install with an alternative install disk, and choose 'server' does that still give me the server kernel?  I would like to install the desktop kernel but without actualyl installing a whole desktop.  I just want x11/evilwm/nvidia/ so i can have my minimal wm but still play games etc.

---

### Post by kuja on 2007-06-21
What I usually use is the minimal install option on the DVD, it defaults to the desktop kernel, and the install is rather light. You'll have to install the X11 (xserver-xorg and xorg metapackages) and evilwm after and such. In such an install the nvidia-drivers won't give you any trouble at all.

---

### Post by jseiser on 2007-06-21
hrm, is there anything similiar that doesnt need a dvd install?  Ubuntu doesnt see my dvd drive, never has.

---

### Post by kuja on 2007-06-21
Still probably easier to just "sudo apt-get install linux-generic"

---

### Post by jseiser on 2007-06-21
That last reply confused me.  I normally server install and then install xorg/wm/fm etc.  Doing so works fine but i cant use nvidia because there is no linux-restricted-modules-server that i can find.    You said to choose minimal from the dvd and it would give me what i want with a desktop kernel.  That would be great but a dvd install isnt feasible.  So i dont get waht the "sudo apt-get install linux-generic" is.  If you are talking about install the generic resctriced modules and use with the server kernel, i tried that and it will not work. :/

---

### Post by kuja on 2007-06-21
No, what I'm recommending is that you install the generic kernel. linux-generic is a metapackage for installing linux-image-generic along with linux-restricted-modules-generic.

---

