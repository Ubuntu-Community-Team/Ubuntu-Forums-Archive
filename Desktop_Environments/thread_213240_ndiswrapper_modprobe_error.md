---
title: "ndiswrapper modprobe error"
date: 2006-07-11
forum: Desktop Environments
---

### Post by cmw000 on 2006-07-11
I'm trying to get ndiswrapper set up and everything is fine until I get to the step where I "sudo modprobe ndiswrapper". Then I get "FATAL: Could not open '/lib/modules/2.6.15-23-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko'"

I suspect 2 things:

1) the ndiswrapper module is missing (when i rmmod ndiswrapper it says not found)

2) i'm missing my kernel source files and they are needed.


I don't know if either of those things are true or pertinent to my error. If someone smart could please help me I would really appreciate it.

---

### Post by cmw000 on 2006-07-11
^

---

### Post by 6and9.42 on 2006-07-11
Ok, I don't know for sure if this will work, as I'm pretty much a linux noob myself :p but! I was having trouble with ndiswrapper myself and was finally able to make it work by removing the included driver file. My wifi card uses the broadcom 43xx drive so I went here and just moved that folder to the root "home" folder:

/lib/modules/(kernel version)/kernel/drivers/net/wireless/

Don't know if that's the problem but it might be worth a try.

g.

---

### Post by sefs on 2006-07-11
1) the first post in this link [http://www.ubuntuforums.org/showthread.php?t=104539&highlight=ndiswrapper+1.7](http://www.ubuntuforums.org/showthread.php?t=104539&highlight=ndiswrapper+1.7)   tells how to set up ndiswrapper

2) this tells how to set up the windows driver with ndiswrapper [http://users.ox.ac.uk/~orie1330/linuxnotes.html](http://users.ox.ac.uk/~orie1330/linuxnotes.html) (scroll down to the wireless part).  

NB step one should give you the two deb files you need in step two.

Hope that helps.

---

