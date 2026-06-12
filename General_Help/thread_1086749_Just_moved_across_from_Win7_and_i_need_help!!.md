---
title: "Just moved across from Win7 and i need help!!"
date: 2009-03-04
forum: General Help
---

### Post by de049 on 2009-03-04
Hi all.

I am back to Ubuntu after 3 years away from it.  So, you could say i am a newb really.

To my problem:  I recently had a 40 GB HDD partitioned into C:\ and D:\ under Windows 7 BETA.  I had all my personal stuff, ie music, images, etc on the D:/ partition.

I then tried to install MacOSX, which required that i formatted the C;| partition as NTFS was not recpgnised.  I ensured the partition being formatted was only C:\, the give away being only 14GBs were being formatted.  The rest of the HDD, D:\ was left as was, NTFS.

I have now installed UBUNTU 8.10 and i cannot get my hands on the content of D:\ for the life of me.  Someone please help.

Here's my output from the "sudo fdisk -l" command:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd2b2d2b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

I have reinstalled Partition Editor and QTparted but i cannot open either.  The Partition Editor in Ubuntu asks for my password, but then nothing else every opens or happens.

Any ideas?

Would really appreciate anyone's time greatly!

ciao

I really hope someone can help

---

### Post by taurus on 2009-03-04
You just wiped out the whole harddrive because you have one partition as root partition, /dev/sda1, and another one as swap, /dev/sda5.  

Did you pick the "use the whole harddrive" when you installed Ubuntu?

---

### Post by emarkay on 2009-03-04
Yea looks like it's been changed from NTFS/FAT32 - did you also format it when installing?   FMI, What's SDA3 and SDA4?

Get the live ISO of "Gparted". it's like a SUPER version of the native Ubuntu partitioner. It wont "unformat" though, but I use it FIRST when doing ANY new partitioning, FWIW.

Hopefully you had backups off-machine...

---

### Post by de049 on 2009-03-05
ok then,

i somehow managed to get Partition Editor to open after 2-3 reboots.  Dont ask me why that is, but it worked anyway.

I see it does look lime my D:\ partition was removed when i installed UBUNTU :(

However, is there no way (via some software tools) to get those files back?  I dont think i selected use entire HDD for installation, i chose the keep partitions option.

Might these files be archived somewhere on the main partition now?

Please advise, loads of personal info on there that i need to recover.

thanks for the help guys.

de049

---

### Post by taurus on 2009-03-05
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

