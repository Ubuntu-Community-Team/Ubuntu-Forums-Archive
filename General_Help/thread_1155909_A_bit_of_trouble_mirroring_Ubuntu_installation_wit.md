---
title: "A bit of trouble mirroring Ubuntu installation with dd"
date: 2009-05-11
forum: General Help
---

### Post by marshall.robert on 2009-05-11
To save myself having to install Ubuntu and all the programs I use I decided to use dd to copy the installation over from an old hard drive to a new one.

They are both 30GB, made using GParted.

But when I boot it fails and tells me to run fsck, which I do with the following result.

[IMG]http://rob-server.co.uk/%7Erob/Ubuntu%2064-bit-2009-05-11-13-40-20.png[/IMG]

I'm guessing it's something to do with superblocks (I know nothing about them), is there any way to fix this/trick it into working?

Any help and suggestions will be greatly appreciated.

-Rob

---

### Post by marshall.robert on 2009-05-11
And so after a bit of searching I found this [http://www.linuxquestions.org/questions/linux-hardware-18/size-in-superblock-is-different-from-the-physical-size-of-the-partition-298175/](http://www.linuxquestions.org/questions/linux-hardware-18/size-in-superblock-is-different-from-the-physical-size-of-the-partition-298175/)

I ran resize2fs /dev/sda1, rebooted and it worked!

So problem solved! :D

---

