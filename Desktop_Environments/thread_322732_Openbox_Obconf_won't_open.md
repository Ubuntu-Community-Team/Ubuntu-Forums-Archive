---
title: "Openbox: Obconf won't open"
date: 2006-12-20
forum: Desktop Environments
---

### Post by gregcha117 on 2006-12-20
I tryed the 

$ cd /usr/lib
$ sudo ln -s libobrender.so libobrender.so.1
$ sudo ln -s libobparser.so libobparser.so.1

fix I found on the bug site but even after that Obconf doesnt seem to open, it goes to 
"starting obconf" but never makes it past that.

Sorry I'm slightly new to Linux, I'm not sure whats going wrong.

---

### Post by gregcha117 on 2006-12-23
nevermind, i used 

sudo -s and got in with root permissions then it worked

---

