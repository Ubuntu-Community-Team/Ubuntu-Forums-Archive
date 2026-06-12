---
title: "Move my Mythbuntu Drive to another computer"
date: 2009-01-11
forum: General Help
---

### Post by munckton on 2009-01-11
Hi Everyone,
I currently have an installation of Mythbuntu on an old P4 computer which is starting to become a little sluggish. I was wondering if I can transplant the drive into an AMD X2 machine without ruining my installation? The AMD will have completely different hardware (there is no raid involved). 

I would not dream of doing this with windows but correct me if I am wrong but Linux should be able to adapt?

Thanks for reading,

Cheers.

---

### Post by andrewc6l on 2009-01-12
The Linux kernel will be able to adapt, but the configuration settings won't. (As a simple example, if the root drive is /dev/sda1 on your old machine but /dev/hda1 on the new machine, you'll be hosed when trying to mount what's in your /etc/fstab.)

It might be easier to back up your existing MythTV config, then set up a new mythbuntu install on the new machine and import the old config. Instructions for that are here:

[http://www.mythtv.org/docs/mythtv-HOWTO-23.html#backupdb](http://www.mythtv.org/docs/mythtv-HOWTO-23.html#backupdb)

and here:
[http://www.mythtv.org/docs/mythtv-HOWTO.html#toc23.7](http://www.mythtv.org/docs/mythtv-HOWTO.html#toc23.7)

---

### Post by munckton on 2009-01-13
Great, I will do it that way. Thanks very much Andrew!

---

### Post by txcrackers on 2009-01-14
To be honest, I've not (yet) had any problems moving drives from old and dying machines to newer hardware. While I will not guarantee it, I don't think it will hurt to at least try it - although you would get more "bang for the buck" using a newer drive, too.

---

