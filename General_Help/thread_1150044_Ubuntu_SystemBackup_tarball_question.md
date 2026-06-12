---
title: "Ubuntu System/Backup tarball question"
date: 2009-05-05
forum: General Help
---

### Post by NiceGuy12 on 2009-05-05
Hi Everyone,

I am relatively new to Ubuntu .. I am in the process of creating a system backup tarball of my current Ubuntu installation.  I would like to store the tarball on a simple liveCD, then use the liveCD environment to partition, format and then extract the system tarball, so as to allow the reduplication/re-creation of my install on another system. Of course the new system will have identical hardware.   
 
So, anyway ... I was firstly wondering if this is even possible?
I notice the Ubuntu uses a feature fairly new to me where UUID are set inside Ubuntu's fstab .. I fear that may be problematic to my brainstorm/design.

Was hoping that someone could confirm?
Thanks

---

### Post by logos34 on 2009-05-05
try [Remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html") (cd/dvd)

or else make a .gz backup image with [Partimage]("http://www.partimage.org/Main_Page") of / partition like I do...you could store it on a usb stick, then boot the live cd on another machine, and 'restore' from the usb to the new machine's hdd.

hope that helps

---

### Post by NiceGuy12 on 2009-05-05
Hi logos34,

Thanks for the reply .. just curious .. are you saying that the UUID labels on each partition are not a problem.

The fstab will be included in the tarball ... and as such will be extracted on the new drive. 

Should I not be concerned that the UUID are being carried over?
Thanks

---

### Post by logos34 on 2009-05-05
yes, when you make an image of a partition, it copies (clones really) eveything exactly, even the UUIDs...Ubuntu uses the uuid rather than the old /dev/sdxy to find partitions. 

You can easily change the uuids on the target machine(s) by running
> 
sudo tune2fs -U random /dev/sda1

or whatever the partition is

(tune2fs is part of **e2fsprogs** package)

remember to update fstab, as well as /boot/grub/menu.lst, of course

---

### Post by NiceGuy12 on 2009-05-06
Thanks logos34,

I booted from a livecd .. and used the blkid command. It displays the UUID for the new partitions.

I simply copied those new UUID (for the new drive) and copied over the relevant UUID to 

```
1. /etc/fstab
2. /boot/grub/menu1.st
```

After words, I saved, rebooted and my drives were found and everything just worked fine.

Thanks again for you time
Take care

---

### Post by logos34 on 2009-05-06
On reading your initial post again, it's clear you weren't really asking for suggestions for alternatives to tarball, but I guess images were on my mind, which is why I responded as I did. Sometimes I have a one-track mind...(BTW, I also make tar.gz backups of my /home--works fine--and periodically make a backup image of / with Partimage, each of which fit on a DVD).

At any rate, yes, if you extracted the *tarball* onto a parition in the new machine, the uuid would be different and hence you'd have to change it just to be able to boot. (If, OTH, you had copied an image to the new machine hdd, then you wouldn't have to change any uuids--it would work right off pretty much without modification (except maybe for install of Grub to MBR), but you might want to change the UUIDs for security/privacy reasons if the machine was destined for another user.

hope that clarfies

enjoy ubuntu

---

