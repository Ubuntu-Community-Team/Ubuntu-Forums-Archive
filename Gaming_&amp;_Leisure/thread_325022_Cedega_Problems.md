---
title: "Cedega Problems"
date: 2006-12-24
forum: Gaming &amp; Leisure
---

### Post by xenoalien on 2006-12-24
I am having trouble installing    cedega-small_5.2.3_all.deb    anyways, when I double click the file it says:

"Cannot open cedega-small_5.2.3_all.deb

The filename "cedega-small_5.2.3_all.deb" indicates that this file is of type "Software package". The contents of the file indicate that the file is of type "plain text document". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "plain text document", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. "

Anyone know how to fix this so that I can install Cedega?
Thanks!

---

### Post by meng on 2006-12-24
Terminal
sudo dpkg -i cedega-small_5.2.3_all.deb

---

### Post by xenoalien on 2006-12-24
Terminal:

xenoalien@xenoalien:~$ cd /home/xenoalien/Desktop
xenoalien@xenoalien:~/Desktop$ sudo dpkg -i cedega-small_5.2.3_all.deb
dpkg-deb: unexpected end of file in version number in cedega-small_5.2.3_all.deb
dpkg: error processing cedega-small_5.2.3_all.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 cedega-small_5.2.3_all.deb
xenoalien@xenoalien:~/Desktop$ 

What am I doing wrong?

---

### Post by meng on 2006-12-24
Perhaps you should ask transgaming about this.

---

### Post by xenoalien on 2006-12-24
alright, thanks

---

### Post by meng on 2006-12-24
Sorry I can't help, I don't use cedega myself. The error messages suggest the file itself is faulty. Maybe transgaming has an ubuntu-specific deb file?

---

