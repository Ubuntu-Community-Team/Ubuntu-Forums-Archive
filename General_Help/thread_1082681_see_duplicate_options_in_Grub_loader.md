---
title: "see duplicate options in Grub loader"
date: 2009-02-28
forum: General Help
---

### Post by WaliWorldX on 2009-02-28
hey everyone, im fairly new to the linux scene (installed Xebian on the original xbox, ipodlinux, been playing around with Backtrack3 for some time) and i just recently installed ubuntu on my main machine. it installed just fine without any problems, except when it restarted to enter the grub loader... it didn't it simple went straight back to windows, (mind you I installed ubuntu on an entirely separate harddrive but it still detected my XP installation as another legitimate OS on my system to add to grub.) but i thought no problem, seeing as how my XP hardrive was still #1 in the boot priority, so i enter my bios and make my ubuntu HDD #1. problem sovled! the only thing now is i have duplacate options, it looks like this. (roughly)

ubuntu kernel 2.6.4.generic 
ubuntu kernel 2.6.4.generic (recovery mode)
ubuntu kernel 2.6.4.generic
ubuntu kernel 2.6.4.generic (recovery mode)

Other Operating Systems:
Windows XP Professional

how can i clean up the duplicates?

Thanks in advance :)

---

### Post by chriskin on 2009-02-28
if what you want is not to see those, you can just erase them in
gksudo gedit /boot/grub/menu.lst

---

### Post by ajgreeny on 2009-02-28
They are probably not duplicates but just different kernels which have been added when you upgraded without removing an older kernel.  Just ignore it; it is useful occasionally to have an older working backup kernel, just in case.

---

### Post by chriskin on 2009-02-28
or at least move it lower in the menu, so that it will be easier for you to reach windows with one button instead of one thousand buttons

---

### Post by sahabcse on 2009-02-28
Hi 

Just comment out unneeded the grub entries in /boot/grub/menu.list.

---

### Post by WaliWorld on 2009-02-28
thanks guys that fixed it. :P (the commenting it out thing) you were right though, it was another older kernal version (-23 and -16).

---

