---
title: "Looking for help with webcam driver install"
date: 2006-07-04
forum: Desktop Environments
---

### Post by far2gud on 2006-07-04
Hi All

I have a chicony twinklecam camera I am trying to get to work using ubuntu. The camera is based on a sonix chipset and I am nearly sure the driver below is the one that I need. Ekiga picks up no device under vl2 or vl4 when using the config druid. My problem is tha I am new to linux and dont really know how to install this driver. Would it be possible for someone to list the commands needed to install this driver or even point me in the right direction. I am using dapper 6.06 with latest updates.

Thanks In Advance

[http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=2](http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=2)

---

### Post by Ramses de Norre on 2006-07-04
Download the file and cd to the directory it's in, then do ```
tar -xzf sn9c102-1.32.tar.gz
cd sn9c102-1.32
make
sudo make install
```
There is no install file with info available so this should do the job, you might need to modprobe a module if it wont work but I can't test this..

---

### Post by far2gud on 2006-07-04
Thanks Ramses,

I will give it ago later and post back!! at work now unfortunatly :(

---

### Post by far2gud on 2006-07-04
Hey Ramses,

The driver in my first post is only supported by kernel 2.6.16 and higher and I think the default dapper one is lower. Should I upgrade my kernal to the newest stable version? or apply this diff file before installing the driver with my current kernel? :confused: 


Thanks Again 

[http://www.linux-projects.org/modules/newbb/viewtopic.php?topic_id=220&forum=3](http://www.linux-projects.org/modules/newbb/viewtopic.php?topic_id=220&forum=3)

---

### Post by far2gud on 2006-07-04
Weird 

I changed usb port and ekiga picked up the camera without driver install so all is good now.

Thanks

---

### Post by koshari on 2006-08-01
how did you get the twinklecam to work in the end, did you load the module?

i have the same cam and cant get it to go,

---

