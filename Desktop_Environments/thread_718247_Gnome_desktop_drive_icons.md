---
title: "Gnome desktop drive icons"
date: 2008-03-07
forum: Desktop Environments
---

### Post by rth on 2008-03-07
I have 3 hard drives in my Ubuntu machine (currently Hardy A6), I've been looking around to find a solution and haven't found one. Anyway, here's what I want:

1. My two "other" drives are internal, sdb and sdc, I do *NOT* want their icons on the Desktop or in Computer or Places
2. I do want removable drive icons to be on the Desktop, so using gconf-editor to remove the icons doesn't help here because it will also remove, say, CDROM icons
3. Essentially I want them to be like sda where it's mounted somewhere (say /var/foldername) and that's it, nowhere else should they show up as they are internal drives

I was reading that mounting the partitions in /mnt/whatever means that they don't have icons on the Desktop, but that didn't work for me. They started as /media/sdb1 and /media/sdc1 as they were set up after installing Ubuntu.

Am I missing something?

---

### Post by mdebusk on 2008-03-08
> **rth said:**
> I was reading that mounting the partitions in /mnt/whatever means that they don't have icons on the Desktop, but that didn't work for me. They started as /media/sdb1 and /media/sdc1 as they were set up after installing Ubuntu.

Did you edit /etc/fstab to reflect the mount points you want?

---

### Post by rth on 2008-03-08
Yes.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc             proc         defaults                    0  0  
# /dev/sda1
UUID=aa7ed884-ed2e-4ab2-beaa-c782ee0787a9  /                 ext3         relatime,errors=remount-ro  0  1
# /dev/sda2
UUID=7247ba41-4cd1-4901-b455-af9d561f4cf3  none              swap         sw                          0  0  
# /dev/sdb1
UUID=83a91bdb-cbdc-488f-aaee-7463715913d7  /mnt/sdb1  ext3         defaults                    0  2
# /dev/sdc1
UUID=96dc2adf-30f4-46a8-8029-112f8e155ee2  /mnt/sdc1   ext3         defaults                    0  2
/dev/scd0                                  /media/cdrom0     udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/fd0                                   /media/floppy0    auto         rw,user,noauto,exec,utf8    0  0 
```
I had it go to /var/something before, then tried /mnt/partition to hide it and left it there for now.

---

### Post by mdebusk on 2008-03-08
> **rth said:**
> Yes.

I'm not intending to insult your intelligence wit this; I just need to cover all the bases.

Did you create new mount points in /mnt and either: unmount the drives from /media and mount them in /mnt; or reboot?

If so, I'm lost.

> I had it go to /var/something before, then tried /mnt/partition to hide it and left it there for now.

That directory is for "variable" data, like log files and temporary files. You probably shouldn't mount drives there. Not that it'll do any harm; it shouldn't.

---

### Post by rth on 2008-03-08
I'm not sure I understand the question... I made folders (/mnt/sdb1 and /mnt/sdc1) and they mount correctly to those folders. There are no corresponding folders in /media called sdb1 and sdc1. I have rebooted a number of times, generally after making a change to /etc/fstab on where I want the drives to mount.

Seeing as there is nothing on the drives, I can remove the partition on each drive and start from scratch. I don't want to open the case and unplug the drives though. :)  If I do that, then what is the proper procedure for adding 2nd/3rd drives to Ubuntu (a lot of the threads and things I see are for dual-booting and a drive is Windows, which is not the case here)?

---

### Post by Keith Hedger on 2008-03-08
This is a bit of kludge but if you right click on the icons and select properties->volume then in the mount options box enter an illegal option say "XXX" the system will not be able to auto mount the drives you can then manually mount them to wherever you wnat

---

### Post by chrisccoulson on 2008-03-08
Mounting under /mnt stops icons appearing on the desktop with Gutsy. However, I've noticed that you're using Hardy. This thread would probably be better off over in the Hardy Heron Development discussion.

---

### Post by mdebusk on 2008-03-08
> **rth said:**
> I made folders (/mnt/sdb1 and /mnt/sdc1) and they mount correctly to those folders.

Let me make sure I understand correctly. The drives are mounted in /mnt and not in /media but the icons still show up on the desktop?

If this is the case, it's a Gnome (or perhaps Nautilus) issue, and I'm clueless as to their inner workings.

> Seeing as there is nothing on the drives, I can remove the partition on each drive and start from scratch. I don't want to open the case and unplug the drives though. :)  If I do that, then what is the proper procedure for adding 2nd/3rd drives to Ubuntu

I don't see anything wrong with what you've done, depending on how well I'm understanding the problem. It's apparent that Ubuntu detected the drives, as it created a UUID in /etc/fstab for each of them, so there's nothing to add. I wonder if there's any chance at all that the UUIDs are incorrect, though.

---

### Post by rth on 2008-03-08
Well, I removed the partitions, rebooted, recreated the partitions and set them in /etc/fstab as before (mounting to /var/whatever) and this time it works. Perhaps it was due to pysdm trying to automount partitions and things? *shrug* I didn't use pysdm this time, I actually removed it from the machine prior to redoing everything.

---

### Post by mdebusk on 2008-03-09
> **rth said:**
> Perhaps it was due to pysdm trying to automount partitions and things? *shrug* I didn't use pysdm this time, I actually removed it from the machine prior to redoing everything.

I hadn't heard of pysdm before. It looks interesting, but if you've had this sort of problem with it I won't mess around with it myself. I don't mind editing fstab.

Glad you've got it straightened out.

---

