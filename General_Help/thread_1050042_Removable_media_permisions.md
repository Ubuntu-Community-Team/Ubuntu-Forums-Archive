---
title: "Removable media permisions"
date: 2009-01-25
forum: General Help
---

### Post by xeol_fr on 2009-01-25
Well I'm still pretty new to Linux, after a couple of months of use I've decided that Linux is the operating system for me and decided to only use Windows if I must (work). After trying several different distributions I have finally decided to stick with Ubuntu. Yesterday I decided to try and give LXDE a try just to see how it is (I like it); but I quickly noticed that after the installation of LXDE I lost access to all of my removable media.

   To begin Brasero will no longer detect my disk drive for burning and even when using sudo I can't change the permissions on the multiple partitions that I have on my 500gig external. Also when add new removable media like USB Thumbdrives I am unable to change permissions on those as well.

Doing *sudo chown -R xeo /media/"drive"* but have no luck.

**Here is an output of ls -l on my media directory:**

xeo@Dynasty:/media$ ls -l
total 104
lrwxrwxrwx  1 root root     6 2008-10-02 07:13 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2008-10-02 07:13 cdrom0
drwxr-xr-x 26 xeo  root  4096 2008-08-16 17:11 disk
dr-xr-xr-x  1 root root 24576 2009-01-25 21:24 Music
drwxrwxrwx  1 root root 65536 2009-01-20 23:25 OverBoost
drwxrwxrwx  1 root root  8192 2009-01-15 18:10 Restore


I'm not sure but it looks as if for the Music drive it looks like only read is allowed for the directory (-xr = no read, execute) please correct me if I am wrong.

**This is my /etc/fstab output:**


[SIZE="1"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ae2d4367-a521-4311-a7cc-db91ac3beefb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ff74b188-fb41-41f5-a18b-3a3335493d7e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
[/SIZE]
Now i'm not sure if it is because the external hard drive is mounted at the moment but I did not see anything in the fstab for it. I would start adding things in there but like I said I am relatively new to Linux and don't just want to start adding things in there without being sure as to what I am doing.

I was hopeing that someone might be able to point me in the right direction in regards to getting back control of my removable media.

Thank you all for your assistance.

---

### Post by mb_webguy on 2009-01-25
Since the permissions on the directory are "r-xr-xr-x", no one (user, group, or others) has write permissions, so simply chown'ing the directory won't matter.  However, chmod'ing the directory to give you write permissions will do the job: "chmod 777 /media/Music" (or the equivalent command for those uncomfortable with binary "chmod ugo+rwx /media/Music") will give everyone full read/write/execute permissions for the directory.

---

### Post by xeol_fr on 2009-01-26
Well I gave "sudo chmod 777 /media/Music" a try and that did not work. I'm still having the same issue with the drive.

---

