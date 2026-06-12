---
title: "Cd is not mounting"
date: 2009-04-18
forum: General Help
---

### Post by GamesForLinux on 2009-04-18
Recently, when I put any kind of cd, music, data, or DVD, the drive will spin it up but then will not mount it, autoplay it or give me any sign that it recognizes the cd. /media/cdrom0 is empty, sound-juicer and rhythmbox don't recgonize it, but vlc will play cds and dvds.
Here is what cat /etc/fstab comes up with:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=214ccc69-a461-43d9-bf8a-e029d2534b05 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=11ac9b62-1d28-4708-b090-c9db05fbfd29 /home           ext3    relatime        0       2
# /dev/sda1
UUID=cee3f1b3-972f-416f-95ac-533f5e930271 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
I've tried mounting manually:
```
$ sudo mount /dev/scd0 /media/cdrom0
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: you must specify the filesystem type
$ sudo mount -t iso9660 /dev/scd0 /media/cdrom0
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
~$ dmesg | tail
[15545.766855] end_request: I/O error, dev sr0, sector 4
[15545.768607] end_request: I/O error, dev sr0, sector 0
[15546.050796] end_request: I/O error, dev sr0, sector 0
[15546.052347] end_request: I/O error, dev sr0, sector 0
[15546.053719] end_request: I/O error, dev sr0, sector 4
[15546.292532] end_request: I/O error, dev sr0, sector 0
[15546.293914] end_request: I/O error, dev sr0, sector 0
[15546.295286] end_request: I/O error, dev sr0, sector 4
[15595.679953] end_request: I/O error, dev sr0, sector 64
[15595.680068] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
$
```
I don't know if this is relevant, but USB drives do mount, but don't auto-open. Also, I have VMware player running Fedora Core 10, and it recognizes disks just fine. :confused:
Any help would be greatly appreciated.

---

### Post by justin_guerin on 2009-04-18
You might check and make sure you have the packages hal and gnome-mount installed.

Also, note that most music CDs and movie DVDs can't be mounted as such.  So the errors you saw attempting to mount the CD below are meaningless if it's strictly a music CD.  Try with a data CD, and see what happens.

If that was a data CD, your drive may be having hardware problems.

---

### Post by GamesForLinux on 2009-04-19
> **justin_guerin said:**
> You might check and make sure you have the packages hal and gnome-mount installed.
These are installed.
> **justin_guerin said:**
> 
Also, note that most music CDs and movie DVDs can't be mounted as such.  So the errors you saw attempting to mount the CD below are meaningless if it's strictly a music CD.  Try with a data CD, and see what happens.

If that was a data CD, your drive may be having hardware problems.

Ok, mounting a data cd manually works. A bit of a pain, but I don't use data cds much anyway.
However, music cds are still a problem - how do I get them recognized so that sound-juicer will see them and be able to extract them? That's something that I do often enough that it's a pain to boot into Fedora just to rip a cd.

---

### Post by gseward on 2009-04-19
I have a similar problem.  I just installed Jaunty 9.04 RC on my  daughters machine and got a call today that she can't read the disk with her wedding pics.  She was able to read this disk with her windows installation, same CD/DVD drive.  I think the disk is a DVD. She has been able to use the drive with a game disk.
Any suggestions would be welcomed.  I have read the  thread.
Thanks

---

### Post by justin_guerin on 2009-04-19
> **GamesForLinux said:**
> These are installed.


Ok, mounting a data cd manually works. A bit of a pain, but I don't use data cds much anyway.
However, music cds are still a problem - how do I get them recognized so that sound-juicer will see them and be able to extract them? That's something that I do often enough that it's a pain to boot into Fedora just to rip a cd.

You might check that your autorun settings are how you want them.  See this page, and see if any settings need to be changed:

[http://propellerheadadmin.com/tutorials/ubuntu/2-change-autorun-settings-in-ubuntu-810](http://propellerheadadmin.com/tutorials/ubuntu/2-change-autorun-settings-in-ubuntu-810)

If those are already set, then insert an audio CD and post the output of /var/log/messages and /var/log/syslog when you do.

---

