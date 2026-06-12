---
title: "Resizing my partition"
date: 2005-10-29
forum: Desktop Environments
---

### Post by Jerrac on 2005-10-29
I want to resize one of my partitions. So I boot into knoppix and try to use qtparted to do so. It won't let me use the resize option. The partition I am resizing is ext3. So, what can I do?

---

### Post by rj686 on 2005-10-29
i used partition magic from windows, I've also heard of people using Gparted off a live cd. What ever you do make sure your root drive isnt mounted

---

### Post by mhancoc7 on 2005-10-29
I have used the Ubuntu 5.04 Install cd to resize my partition. After I resized it using the guided partitioner I simply exited the installation. I may be forgetting some steps, but I remember it being a lot simplier than I expected. 

God Bless, Jereme

---

### Post by HermanAB on 2005-10-29
Well, what error do you get?

Note that knoppix starts up with the disk partitions unmounted, but if you would click on a disk icon, then it will get mounted and you cannot resize a mounted partition.

You can see what is mounted with - drum roll - wait for it - the mount command:
# mount

If any partitions are mounted, umount them manually.

Cheers,

Herman
[http://www.AerospaceSoftware.com/linuxhowtos.html](http://www.AerospaceSoftware.com/linuxhowtos.html)

---

### Post by Jerrac on 2005-10-29
Eh, I made sure the partition was not mounted...

Would use partiton magic, but I do not have windows installed. :D

I will try the install cd tomorrow

---

