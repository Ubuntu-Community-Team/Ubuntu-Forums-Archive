---
title: "mounting disks at startup, lose desktop icons"
date: 2009-05-07
forum: General Help
---

### Post by mattyj on 2009-05-07
Hello,

Using ubuntu 8.10 still 

I just reinstalled ubuntu on my sda1 and have two other drives I would like to mount at startup, sdb1 and sdc1.

mj@mj-desktop:~$ blkid
/dev/sda1: UUID="d46bf7f5-068b-4204-9eb3-b39539acd582" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="6c2e2e8b-8228-48d5-af9e-3ee466efd719" 
/dev/sdb1: LABEL="sdb1" UUID="d59347b1-8a2a-4608-ba7c-6f163d175c98" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: LABEL="sdc1" UUID="90ea9d23-8de4-4cf3-a913-7702f60bdec3" SEC_TYPE="ext2" TYPE="ext3" 

Currently to mount the disks I have to go to places/removable media and they mount...

If I edit my fstab to the following...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d46bf7f5-068b-4204-9eb3-b39539acd582 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=6c2e2e8b-8228-48d5-af9e-3ee466efd719 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sdb1
UUID=d59347b1-8a2a-4608-ba7c-6f163d175c98 /media/sdb1 ext3 exec,relatime 0 2
# /dev/sdc1
UUID=90ea9d23-8de4-4cf3-a913-7702f60bdec3 /media/sdc1 ext3 exec,relatime 0 2



Then the icons no longer show up on the desktop for any drives or inserted CDs and there is strange behavior in terms of recongition of the files on those disks...

---

### Post by logos34 on 2009-05-07
> # /dev/sdb1
UUID=d59347b1-8a2a-4608-ba7c-6f163d175c98 /media/sdb1 ext3 exec,relatime 0 2
# /dev/sdc1
UUID=90ea9d23-8de4-4cf3-a913-7702f60bdec3 /media/sdc1 ext3 exec,relatime 0 2

'exec' option is already the default IIRC, so you really don't need it

Did you create the mount points?

ls -l /media

sudo mkdir /media/sdc1

---

### Post by mattyj on 2009-05-07
> **logos34 said:**
> 'exec' option is already the default IIRC, so you really don't need it

Did you create the mount points?

ls -l /media

sudo mkdir /media/sdc1


Hello,

Yes, I can get them to mount fine in /home/mj or /media as I define, but when I do so I no longer see the disk icons on the desktop like I did before I uninstalled.  Also, when I insert a CD, it no longer pops up on the desktop.

If I revert to the default fstab the all of these features return.  Any ideas?

Thank You.

MJ

---

### Post by mcduck on 2009-05-07
> **mattyj said:**
> Hello,

Yes, I can get them to mount fine in /home/mj or /media as I define, but when I do so I no longer see the disk icons on the desktop like I did before I uninstalled.  Also, when I insert a CD, it no longer pops up on the desktop.

If I revert to the default fstab the all of these features return.  Any ideas?

Thank You.

MJ

IF you can't see CD's or other removable drives on desktop either then it's not fstab issue. Are you sure oyu haven't at some point disbaled drive incons on desktop with gconf-editor?

Hit Alt-F2 and run "gconf-editor", browse to apps/nautilus/desktop and make sure "volumes_visible" is enabled.

---

### Post by logos34 on 2009-05-07
> **mattyj said:**
> I can get them to mount fine in /home/mj or /media as I define, but when I do so I no longer see the disk icons on the desktop like I did before I uninstalled.  Also, when I insert a CD, it no longer pops up on the desktop.

If I revert to the default fstab the all of these features return.  Any ideas?

Your initial post is a little confusing.  But given your additional comments I would tend to agree with mcduck's suggestion, except you say everything works fine when you go back to original fstab. So exactly which 'default fstab' do you mean? Clarify please

---

### Post by mattyj on 2009-05-07
> **logos34 said:**
> Your initial post is a little confusing.  But given your additional comments I would tend to agree with mcduck's suggestion, except you say everything works fine when you go back to original fstab. So exactly which 'default fstab' do you mean? Clarify please

Thank you for your help.  Sorry for the confusion.  I initially had some difficulty mounting the drives at specified locations, but it was a typo.  Now the main issue is that when I try to use fstab to mount the drives at startup, I lose the icons.

I start with ...

fstab, unedited...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d46bf7f5-068b-4204-9eb3-b39539acd582 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=6c2e2e8b-8228-48d5-af9e-3ee466efd719 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


In this setting if I go to Places/RemoveableMedia and select sdb1 or sdb1 they are mounted (I do have to enter a password).

If I then change my fstab to:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d46bf7f5-068b-4204-9eb3-b39539acd582 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=6c2e2e8b-8228-48d5-af9e-3ee466efd719 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sdb1
UUID=d59347b1-8a2a-4608-ba7c-6f163d175c98 /home/mj/sdb1 ext3 exec,relatime 0 2
# /dev/sdc1
UUID=90ea9d23-8de4-4cf3-a913-7702f60bdec3 /home/mj/sdc1 ext3 exec,relatime 0 2

Then I no longer get those icons on the desktop, and when I insert a CD it does not come up on the desktop.   That is the only thing that I am changing.  I agree that it is strange as I did not think that fstab controlled this.

---

### Post by mattyj on 2009-05-07
> **mattyj said:**
> Thank you for your help.  Sorry for the confusion.  I initially had some difficulty mounting the drives at specified locations, but it was a typo.  Now the main issue is that when I try to use fstab to mount the drives at startup, I lose the icons.

I start with ...

fstab, unedited...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d46bf7f5-068b-4204-9eb3-b39539acd582 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=6c2e2e8b-8228-48d5-af9e-3ee466efd719 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


In this setting if I go to Places/RemoveableMedia and select sdb1 or sdb1 they are mounted (I do have to enter a password).

If I then change my fstab to:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d46bf7f5-068b-4204-9eb3-b39539acd582 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=6c2e2e8b-8228-48d5-af9e-3ee466efd719 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sdb1
UUID=d59347b1-8a2a-4608-ba7c-6f163d175c98 /home/mj/sdb1 ext3 exec,relatime 0 2
# /dev/sdc1
UUID=90ea9d23-8de4-4cf3-a913-7702f60bdec3 /home/mj/sdc1 ext3 exec,relatime 0 2

Then I no longer get those icons on the desktop, and when I insert a CD it does not come up on the desktop.   That is the only thing that I am changing.  I agree that it is strange as I did not think that fstab controlled this.

I am not positive, as I changed a few things, but I think it had to do with the permissions set on the drives/locations mounted to.  I changed those to 0777 and restarted, and now it gives me the icons again.

I will repost if I figure it out more explicitly, but it was some strange behavior.

Thank You for your help.

MJ

---

### Post by logos34 on 2009-05-07
post your

sudo fdisk -l

---

### Post by mattyj on 2009-05-08
> **logos34 said:**
> post your

sudo fdisk -l

mj@mj-desktop:~$ sudo fdisk -l

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00006e48

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17495   140528556   83  Linux
/dev/sda2           17496       18241     5992245    5  Extended
/dev/sda5           17496       18241     5992213+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e2da3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xde6c2522

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux
mj@mj-desktop:~$

---

### Post by logos34 on 2009-05-08
these *are* external usb drives, right?

---

### Post by mcduck on 2009-05-08
> **mattyj said:**
> Thank you for your help.  Sorry for the confusion.  I initially had some difficulty mounting the drives at specified locations, but it was a typo.  Now the main issue is that when I try to use fstab to mount the drives at startup, I lose the icons.

I start with ...

fstab, unedited...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d46bf7f5-068b-4204-9eb3-b39539acd582 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=6c2e2e8b-8228-48d5-af9e-3ee466efd719 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


In this setting if I go to Places/RemoveableMedia and select sdb1 or sdb1 they are mounted (I do have to enter a password).

If I then change my fstab to:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d46bf7f5-068b-4204-9eb3-b39539acd582 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=6c2e2e8b-8228-48d5-af9e-3ee466efd719 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sdb1
UUID=d59347b1-8a2a-4608-ba7c-6f163d175c98 /home/mj/sdb1 ext3 exec,relatime 0 2
# /dev/sdc1
UUID=90ea9d23-8de4-4cf3-a913-7702f60bdec3 /home/mj/sdc1 ext3 exec,relatime 0 2

Then I no longer get those icons on the desktop, and when I insert a CD it does not come up on the desktop.   That is the only thing that I am changing.  I agree that it is strange as I did not think that fstab controlled this.

Your first fstab has no entries for these partitions. That means they are not mounted by fstab but in the same way removable drives are handled.

In the second fstab, you mount the drives under /home. Only drives mounted under /media will appear on desktop.

---

### Post by logos34 on 2009-05-08
> **mcduck said:**
> Only drives mounted under /media will appear on desktop.

I didn't know that! (probably because I never mount enything in home).  Learn something new every day...

I wonder if a good compromise for mattyi would be to have them [automount using labels (e2label)]("https://help.ubuntu.com/community/RenameUSBDrive#Basics")...that way you get same, fixed mountpoint (in /media by label name) every boot, AND the desktop icons

---

### Post by dcstar on 2009-05-08
If you want your removable disks to be mounted **and** on the desktop, do **NOT** touch the fstab file but simply use the Configuration Editor and set this key:

/apps/nautilus/preferences/media_automount

*"If set to true, then Nautilus will automatically mount media such as user-visible hard disks and removable media on start-up and media insertion."*

---

