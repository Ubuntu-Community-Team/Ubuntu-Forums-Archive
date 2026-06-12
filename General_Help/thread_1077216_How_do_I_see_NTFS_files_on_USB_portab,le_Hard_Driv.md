---
title: "How do I see NTFS files on USB portab,le Hard Drive"
date: 2009-02-22
forum: General Help
---

### Post by chipppy on 2009-02-22
I want to transfer a huge amount of files from my XP machine to my new Mythbunutu machine.  I dont have either networked so I want to use my USB 250GB portable hard drive.

I cannot get this drive to mount/see it on the mythbunutu system.

Anyone have any idea of how to mount this USB HDD so I can copy the files into the video directory?

I have successfully used my 16GB USB stick to transfer one video as a test, but I believe USB sticks use FAT to store data not NTFS.

Cheers
chipppy

---

### Post by SunnyRabbiera on 2009-02-22
try ntfs3G and ntfs config, I dont know if they are preinstalled though in mythbuntu...
I know both come with standard Ubuntu though.

---

### Post by chipppy on 2009-02-23
I have installed mountmanager and ntfs config tool.  Still no luck.  I cannot even see the portable HDD in the file system.  

Any ideas where to start.  This portable HDD does automagic connect to the XP system.

---

### Post by mb_webguy on 2009-02-23
Plug in the drive and then type "sudo fdisk -l" in the terminal.  If you see an entry corresponding to the drive, then it's just not being automatically mounted.  You can then mount it using "sudo mkdir /media/usb && sudo mount -t ntfs /dev/*device_id* /media/usb".

---

### Post by chipppy on 2009-02-24
With the portable HDD connected and the pretty blue light on I tried the **sudo fdisk -l**, and the portable HDD is not seen by my linux machine.

Any ideas?  I am completly stumped by this one.

Cheers
chipppy

---

