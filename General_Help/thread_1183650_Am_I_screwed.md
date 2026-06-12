---
title: "Am I screwed?"
date: 2009-06-10
forum: General Help
---

### Post by silverfire675 on 2009-06-10
Long story short.  I had ubuntu, I deleted it and installed vista.  So vista is on my computer currently but GRUB is hanging me up and not letting me go through.  I cannot boot vista from the cd's and I cant think of anything to do. How did grub not get wiped out when I erased the whole Disk b4 reinstalling vista...

---

### Post by mixmaster on 2009-06-10
Sounds like you had grub installed in the mbr.  You can repair this with fdisk on a windows syustem (fdisk /mbr, from memory) or you can do it from the recovery console

---

### Post by yaroto98 on 2009-06-10
Yup, the Vista disk should have recover tools, if you google them you can run a command something like "fixmbr" or "auto-fixmbr" that should do it for you.

Found the [tutorial]("http://www.lancelhoff.com/how-to-fix-vista-mbr-repair-broken-vista/")

---

### Post by ajgreeny on 2009-06-10
> **mixmaster said:**
> Sounds like you had grub installed in the mbr.  You can repair this with fdisk on a windows syustem (fdisk /mbr, from memory) or you can do it from the recovery console
Surely if grub was on the MBR it would have been overwritten with the windows MBR by the Vista install.  It could be that your grub was on a different disk, or partition to the MBR, or that you had a separate /boot partition.

Finally, if you have more than one disk in the machine, make sure that the BIOS is set to boot from the correct one.

---

### Post by silverfire675 on 2009-06-10
OK. Update!  I reinstalled ubuntu and now am dual booting it.  I need a program to delete the ubuntu partition and give that space to windows. 
 
I tried your commands to repair the MBR but it won't work.  Mainly cause I dun have a live cd.  I have this recovery cd that you use to reinstal windows but its not like the usual version.   So basicly How would i go about deleteing grub through vista without the live cd?  Thanks for your help.

---

### Post by yaroto98 on 2009-06-10
Without being there and seeing what's exactly going on, here's the shortcut.

Backup everything you want to keep.
Boot to the Ubuntu live-cd (w/out changes to your computer)
System->Administration->Partition Editor
Delete every partition, apply, you should only see "free space"
pop your vista disk back in and reinstall.

---

### Post by raymondh on 2009-06-10
> **yaroto98 said:**
> Without being there and seeing what's exactly going on, here's the shortcut.

Backup everything you want to keep.
Boot to the Ubuntu live-cd (w/out changes to your computer)
System->Administration->Partition Editor
Delete every partition, apply, you should only see "free space"
pop your vista disk back in and reinstall.

Just curious .... if you delete the pre-installed recover partition and you only have a Vista recovery CD ... will you still be able to re-install Vista?

---

### Post by silverfire675 on 2009-06-10
Yes I can wipe the whole drive and reinstall vista.  Its just that grub has INFECTED my system and I cannut get it off :(

---

### Post by silverfire675 on 2009-06-10
YEA! easybdd was able to switch it. Now I just need a good program to delete the ubuntu partition.

---

### Post by raymondh on 2009-06-10
> **silverfire675 said:**
> OK. Update!  I reinstalled ubuntu and now am dual booting it.  I need a program to delete the ubuntu partition and give that space to windows. 
I tried your commands to repair the MBR but it won't work.  Mainly cause I dun have a live cd.  I have this recovery cd that you use to reinstal windows but its not like the usual version.   So basicly How would i go about deleteing grub through vista without the live cd?  Thanks for your help.


Hello silverfire,

When you're dual-booting, are you able to access/boot into the Vista OS?

ajgreeny has a point.  Re-installing Vista the first time should/would have overwritten the  GRUB in the MBR ... unless, you have GRUB on a separate partition, disk or /boot is separate when you installed Ubuntu.

If you still have Ubuntu .... access a terminal and post the outputs of 

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

For alternatives, you may want to consider supergrubdisk

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Also, Herman (a forum member) has detailed documentary about supergrubdisk as well as instructions you may want to read before proceeding

[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

Let the forum know how goes.

Good luck,

---

### Post by silverfire675 on 2009-06-10
Well so far Easybcd reports to switching the bootloader and I am now in the process of reformatting a part of the drive.  I think it should work now, But i need to restart and check.  Thx!

---

### Post by raymondh on 2009-06-10
> **silverfire675 said:**
> YEA! easybdd was able to switch it. Now I just need a good program to delete the ubuntu partition.

cool ....

you can use Vista's disk management tool to delete and expand the vista partition or you can download and burn gparted to use as well.

Remember though that you may have to fix the vista bootloader again as you delete Ubuntu.

Congratulations.

---

