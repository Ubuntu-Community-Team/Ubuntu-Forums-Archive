---
title: "Problems with booting with windows hd in"
date: 2006-07-19
forum: Desktop Environments
---

### Post by doomstone on 2006-07-19
I have just installed Ubuntu, before where i running windows.
i have 2 hard drives (2 WD sata, 250gb and 300gb)
Before i installed Ubuntu did i do a backup of all my movies and music of my second hard drive (300gb), and i totaly deleted all where where on my 250gb hdd. under the install of ubuntu had i removed my 300gb harddrive from the computer to be abselut sure that i did not delete anyting from it.

Now do i have Ubuntu up and running with drives and all that, so i shutdown the pc and connected my 300gb hd yet again.

But Ubuntu won't start up with 300gb hd in, it have 3 NTFS partitions and i think this is why.

i get the error
```
Target file system doesn't have /sbin/init
BusyBox v1.01 (Debian 1:1.01-4Ubuntu4) Built-in shell (ash)

/bin/sh can't access tty; job control turned off
```

What can i do can i can boot up when my NTFS hd in, so i can recover my files?

---

### Post by geco on 2006-07-19
> **doomstone said:**
> I have just installed Ubuntu, before where i running windows.
i have 2 hard drives (2 WD sata, 250gb and 300gb)
Before i installed Ubuntu did i do a backup of all my movies and music of my second hard drive (300gb), and i totaly deleted all where where on my 250gb hdd. under the install of ubuntu had i removed my 300gb harddrive from the computer to be abselut sure that i did not delete anyting from it.

Now do i have Ubuntu up and running with drives and all that, so i shutdown the pc and connected my 300gb hd yet again.

But Ubuntu won't start up with 300gb hd in, it have 3 NTFS partitions and i think this is why.

i get the error
```
Target file system doesn't have /sbin/init
BusyBox v1.01 (Debian 1:1.01-4Ubuntu4) Built-in shell (ash)

/bin/sh can't access tty; job control turned off
```

What can i do can i can boot up when my NTFS hd in, so i can recover my files?
check out the boot drives from BIOS...

---

### Post by cotcot on 2006-07-19
Your files should be accessible with a liveCD. Have you tried that ?

---

### Post by doomstone on 2006-07-19
My bios is set to boot on cd first, the my 250gb hd (The one with linux) and then the 300gb

---

### Post by goobers on 2006-07-19
Maybe its to do with the master/slave settings of you harddrives? make sure the jumper on the linux one is set to master, and the ntfs one is set to slave?

---

### Post by doomstone on 2006-07-19
Hmm i will try that with the live cd now.
But i don't think it is becaus it trys to boot on rong hdd, becaus i can see that the Ubuntu startup comes and then i get the error at "Mounting root file system"

---

### Post by doomstone on 2006-07-19
Ok i have just tryed to boot on the Live CD with both harddrives connected. and it boots without any problem, but I can't read the hd's.

Sata hard drives do not need jumbers, becaus they are on a single cable.
my 250gb is in sata1
my 300gb in in sata2

(Would more information about the error help? i have tryed to find it, but i can't locate the startup log)

---

### Post by Ramses de Norre on 2006-07-19
It's /var/log/messages.
Why can't you read the drives? What's the error when you try to mount them?

---

### Post by doomstone on 2006-07-19
When i boot up on the live se and select "Places -> Computer" can i see "Cd rom", "243 gb" "7 gb", "10 gb" and "Media 2"
243gb is my /home
7gb is my swap
10gb is my /
and Media 2 is my NTFS hd

when i click on "243 gb" (my /home) i get the message

```
Unable to mount the selected volume

error: device /dev/sda6 is not removable
error: could not execute pmount
```

I where unable to find what you might would need from
/var/log/messages
so i have uploaded the entire file to 
[http://62.242.80.42/linux.txt](http://62.242.80.42/linux.txt)

---

### Post by doomstone on 2006-07-19
If it can help.. this is the layout of my 250gb hd (The one with linux on)

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10241406   83  Linux
/dev/sda2            1276       30401   233954595    5  Extended
/dev/sda5            1276        1912     5116671   82  Linux swap / Solaris
/dev/sda6            1913       30401   228837861   83  Linux

---

### Post by doomstone on 2006-07-19
Reinstalling with the 2 hd connedted worked

---

