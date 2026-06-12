---
title: "No xorg.conf?"
date: 2006-05-20
forum: Desktop Environments
---

### Post by Exuro on 2006-05-20
I've beent trying to install Ubuntu Breezy Badger 5.10 on my machine, but it keeps saying that X-server failed to load (giving the "No device detected" and "No screens found" errors).  I've read around, and it seems like all the answers have said to edit the xorg.conf file.  Here's the weird thing though: I can't edit mine!  It's like it's not there.  I try "cd /ect", and it says that the directory doesn't exist.  But, when I type "locate xorg.conf", it says that "/ect/X11/xorg.conf" is one of the matches!  But, if I type "vim /ect/X11/xorg.conf" it says it's a "new file" (because it doesn't exist?). I'm really confused, and if anyone could help that'd be great. My video device is an onboard ATI Radeon XPress 200 series.  I'm totally new to Linux too, so detailed explainations (including what commands to use) would be great. Thanks!

---

### Post by manicka on 2006-05-20
try the directory 

/etc

---

### Post by Exuro on 2006-05-20
[QUOTE=manicka]try the directory 

/etc[/QUOTE]
:confused:
What? If I type in "/ect" it says "not a file or directory". Is that what you were talking about?

---

### Post by Ramses de Norre on 2006-05-20
There is quite a difference between "etc" and "ect"...

---

### Post by Exuro on 2006-05-20
Wow, that's what I get for not sleeping... Thanks!

---

