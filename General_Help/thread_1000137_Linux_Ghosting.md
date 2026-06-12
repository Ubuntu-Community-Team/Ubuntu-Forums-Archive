---
title: "Linux Ghosting"
date: 2008-12-02
forum: General Help
---

### Post by dmcdaniel on 2008-12-02
Hello Everyone,

I have 10 machines that I will be building all using EXACTLY the same parts with EXACTLY the same size hard drives. I use a MAIN machine as of right now that has the exact same parts as the 10 new machines. This machine has a FRESH build of Ubuntu 8.04 on it with all of the updates and programs installed that we need. 

I would like to Ghost down this machine and place it on the others. What program's would you recommend that are the easiest to use for a Novice (but definitely not an expert) Linux user? I tried G4L but it would not work properly for me. It stated my backup drive didn't have enough space (Image is 10 gigs and Backup drive is 250 Gigs).

Thanks for your time,
dmcdaniel

---

### Post by Zorael on 2008-12-02
I used [Partimage](http://en.wikipedia.org/wiki/Partimage) to back up my service partition, and I found it very straight-forward. It's in  the universe repositories, package name [**partimage**](http://packages.ubuntu.com/intrepid/partimage).

edit: And if you choose some modicum of compression, that should get the image size down if you have empty space on your source partition.

---

### Post by DancingMan on 2008-12-02
<delete my post pls>

---

### Post by binbash on 2008-12-02
you can try clonezilla

---

### Post by linux_tech on 2008-12-02
Clonezilla works good
[http://www.clonezilla.org/](http://www.clonezilla.org/)
Another is Disk copy, you make a cd which I believe is bootable.
With both drives attached you boot to the disk and the utiity allows you to make exact copies of the hard drive you want to image. 
[http://www.easeus.com/disk-copy/download.htm](http://www.easeus.com/disk-copy/download.htm)

---

### Post by Graham1 on 2008-12-02
Another choice of software is PING (Partimage Is Not Ghost). Out of those mentioned, I would say that Partimage is the easiest to use (only two screens). PING on the other hand is more similar to Ghost in how your create images (or at least I thought so). 

If you haven't found it already, I would highly recommend "Parted Magic". This boot cd allow you to run Partimage and G4L as well as GParted for partitioning.

:)

---

### Post by Graham1 on 2008-12-02
Please delete (double post).

---

### Post by dmcdaniel on 2008-12-03
Thanks to everyone who has posted so far. I have heard of a few of those but wasn't sure which would be best. I will test them and let you all know what I choose. 

Thanks,
dmcdaniel

---

### Post by Graham1 on 2008-12-07
Hi dmcdaniel

Please do report back with your choice and your reasons for choosing that particular product. I am also testing various cloning software and would be interested in your opinion.

:)

---

### Post by hambone79 on 2008-12-07
I will have to put my vote on clonezilla. I have used it in the past to clone computers and for moving hard drive images when I drive begins to fail. It works great and I have never lost data with it.

---

### Post by Ellaine on 2008-12-07
Will partimage work in 64 bit Ubuntu? I've been using Acronis TrueImage bootdisk, but would like to try partimage. Thanks.

---

### Post by Graham1 on 2008-12-08
> **Ellaine said:**
> Will partimage work in 64 bit Ubuntu? I've been using Acronis TrueImage bootdisk, but would like to try partimage. Thanks.

I can't see why not but don't hold me to that :). I've always used Partimage for imaging/restoring 32-bit OS's. Your best bet is to download "Parted Magic" (which inc. Partimage 0.6.7) and maybe post your comment in Parted Magic's forum. Btw, is Acronis TrueImage bootdisk a paid for product or a cut down version?

:)

---

### Post by moorsey on 2009-01-06
just related on this, sorry to drag it up, but how does Linux handle being imaged to multiple PCs as far as PC name conflicts for example?

Also, does it have an equivalent of the Windows SID (security identifier)?  This has to be removed before a Windows image is put on multiple PCs for example.

Any reference for this kind of stuff would be appreciated!

---

