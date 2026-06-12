---
title: "Speeding up Flash"
date: 2006-05-23
forum: Desktop Environments
---

### Post by suspend on 2006-05-23
I'm running XUbuntu on an old P2-400 with 400MB of RAM.  My swap is swank.  My little girl wants to play flash apps from nick jr.  I got it installed, but they run like a dog.  Is there something I can do to either overclock the CPU in linux, like a win app, or something to tweak flash?  Oh, the browser on the box is Firefox.  Prethanks all.

---

### Post by Kethinov on 2006-05-23
I don't think that you can. Flash performance on Linux has always been somewhat atrocious, thanks to poor support of Linux by Macromedia.

---

### Post by suspend on 2006-05-24
I figured it was something like that.  Thanks.

---

### Post by adamkane on 2006-05-24
Ouch. This will help (a little).

```

sudo apt-get install linux-686 linux-headers-686

``` 
Reboot.

This installs some faster (optimized) kernel files. 

Ubuntu ships with generic kernel files, which makes Ubuntu seem slow, so you should install the correct kernel files for your system. (Don't ask me what a kernel is.)

Installing xubuntu doesn't really help. If you use applications that bog down your system, your system will be bogged down no matter which ubuntu you install.

Xubuntu isn't a solution for speed problems. Everyone needs to stop suggesting xubuntu for this type of problem. Xubuntu is more about taste.

---

