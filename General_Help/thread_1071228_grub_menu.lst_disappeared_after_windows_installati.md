---
title: "grub menu.lst disappeared after windows installation"
date: 2009-02-15
forum: General Help
---

### Post by futui tuam matrem on 2009-02-15
I have just finished a dual install of Intrepid and Vista on my friends box. I managed to get grub reinstalled to the mbr using the ubuntu livecd but now I can't get either OS to boot. When I power on, I just get a grub command prompt. I poked around some with the livecd again and although grub is installed, there is no menu.lst or grub.conf to be seen anywhere. Google didn't seem to turn up anyone with this specific problem. Any ideas on how to get my menu.lst back? Thanks in advance.

---

### Post by jwbrase on 2009-02-15
Now I'm very new to this, but I think I recall hearing mentioned somewhere that Windows wipes all other bootloaders it finds when it installs or something.

---

### Post by futui tuam matrem on 2009-02-16
Yes, windows wipes the MBR when you do an install. I have since reinstalled Grub, but for some reason there is no grub.conf or menu.lst file. Is there a simple way to get it to make one for itself, or will I have to write one out manually? Any help would be appreciated. Thanks.

---

### Post by casanostra on 2009-02-16
I remember I did this once, but not exactly how. My guess is that you'll be able to both boot the two systems from the command line, and also write a new menu.lst.

[This article]("http://www.linuxjournal.com/node/4622/print") may get you started.

---

