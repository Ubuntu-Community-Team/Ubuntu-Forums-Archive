---
title: "Mounting a windows partition"
date: 2009-01-02
forum: General Help
---

### Post by xct9-3 on 2009-01-02
I installed ubuntu 8.10 on a different partition from my vista install, however I cannot get back into windows after the install.  Grub does not recognize this it as a bootable partition, nor do a few other boot loaders I've tried.

I've been trying to mount the partition used for vista in order to pull some data at least, and have not been able to.  Yet another partition I setup exclusively for data which was frequently used with vista is mountable. 

Here is the information I've gathered, sda6 being the partition in question.

kyle@unixbuild:~$ sudo fdisk -l
[sudo] password for kyle: 

Disk /dev/sda: 100.0 GB, 100030242816 bytes
240 heads, 63 sectors/track, 12921 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x2c8fa2c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1355    10243768+  83  Linux
/dev/sda2            1356       12921    87438929    f  W95 Ext'd (LBA)
/dev/sda5            1356        6773    40960048+   7  HPFS/NTFS
/dev/sda6            6774       12921    46478848+   7  HPFS/NTFS


Gparted sees sda6 as a 44 Gb partition of an unknown file system, although I'm sure it was in NTFS, like sda5 which is mountable.


Any ideas on how to mount sda6?

---

### Post by xenolalia on 2009-01-02
When you try to mount the partition, what happens?

I had a similar problem a while ago, though mine was with a much earlier version of windows.  If you still have your install cd, you probably ought to be able to use that to repair your vista installation.  If not, you can try making a vista recovery disk: 

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

and at the command line, running the commands "fixboot" and "fixmbr" to repair vista.

I don't have too much experience in this department, but I think that should do it.

Good luck!
Xenolalia

---

### Post by xct9-3 on 2009-01-02
It doesn't give me the option to mount the partition, I'm going to try the recovery disc, great idea thanks!

---

### Post by xct9-3 on 2009-01-02
Windows does not recognize the OS at all when I try to repair it. Is there anyway to "force" mount a partition? I'm starting to think it was erased but I would at least like to check if there are any files on it.

Thank you

---

### Post by xct9-3 on 2009-01-03
Bump, any ideas on how to force mount the partition?

---

### Post by Moop on 2009-01-03
Use the partition editor on the live cd or install gparted in Ubuntu. That should show you your partitions and if there is data on them.

---

### Post by xenolalia on 2009-01-03
Yes.  I agree.  Using a live cd would be a good way of determining if your vista installation is still there.  You could also try burning a gparted live cd (which I have always had more luck with).  Or . . . you could try browsing bootdisk.com to see if there are any handy bootdisks you can download there that might help you to restore vista.  I'm playing around with the vista recovery cd to see if I can figure out what's wrong.  I'll get back to you shortly.

Good luck!
Xenolalia

P.S. One other option is creating a windows pe disk -- basically a cut down, command line version of windows (pe stands for pre-installation environment).  Here are instructions: [http://www.windowsnetworking.com/articles_tutorials/Deploying-Vista-Part11.html](http://www.windowsnetworking.com/articles_tutorials/Deploying-Vista-Part11.html)

P.P.S. If you don't have access to windows pe, you could also try bart pe (a comparable tool).  Here are instructions: [http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

---

