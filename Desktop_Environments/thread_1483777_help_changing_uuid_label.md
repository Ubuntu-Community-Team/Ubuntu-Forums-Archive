---
title: "help changing uuid label"
date: 2010-05-15
forum: Desktop Environments
---

### Post by skaramanger on 2010-05-15
Greetings,

I recently changed a mount point for one of my partitions. As a result, I get two entries in nautilus. One under to old LABEL which is accessible and the new label which when clicked on gives an error message that the the mountpoint is either already mounted or busy.  So I went searching the forums and came up with some data to share concerning my system. It follows:


```
[mydsktp ~]$ sudo blkid -c /dev/null
/dev/sda1: LABEL="root" UUID="0eaa02f9-8d4a-40b6-b282-9001ca383700" TYPE="ext3" 
/dev/sda5: LABEL="Home" UUID="b34aa478-7495-4e4a-bfba-f31d24d268eb" TYPE="ext3" 
/dev/sda6: UUID="e3c944e6-00af-44f5-b937-6d5999325148" TYPE="swap" 
/dev/sda7: LABEL="MyDwnlds" UUID="969e7370-b0e5-4127-85e1-745cb500d6b8" TYPE="ext3" 
/dev/sdc5: LABEL="My_Book" UUID="0a3b8fc4-062f-4ff6-81d5-f3ba03f1d425" TYPE="ext3" 
 [mydsktp~]$ 
```

This is a cat of my fstab file:

```
 /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=0eaa02f9-8d4a-40b6-b282-9001ca383700 /               ext3    errors=remount-ro 0       1
# MyDwnlds was on /dev/sda7 during installation
UUID=969e7370-b0e5-4127-85e1-745cb500d6b8 /media/Downloads       ext3    rw,users,auto,user_xattr        0       2
# /home was on /dev/sda5 during installation
UUID=b34aa478-7495-4e4a-bfba-f31d24d268eb /home           ext3    defaults,user_xattr        0       2
# swap was on /dev/sda6 during installation
UUID=e3c944e6-00af-44f5-b937-6d5999325148 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# UUID=0a3b8fc4-062f-4ff6-81d5-f3ba03f1d425	/media/My_Book	ext3	rw,users,auto	0	0


```

I changed my mount point from /MyDwnlds to /media/Downloads.  I know but I was tired the night I did the install and forgot to put MyDwnlds under the media folder.  So I am fixing it now :).  And last but not least below is a screenshot of the filemanager.  I have rebooted a couple of times but it stills shows the two entries.  Is there a way to fix this in nautilus or change the Label using blkid?

Thanks in Advance
skaramanger

---

### Post by kio_http on 2010-05-15
Try deleting nautilus's saved configuration. This will cause nautilus to auto reconfigure itself.

Open your terminal application

```
rm -rf .nautilus
```

[COLOR=DarkRed]Note: This will cause you to lose all settings you have put in nautilus.[/COLOR]

---

### Post by mcduck on 2010-05-15
Have you tried with more basic mount options? 
```

UUID=969e7370-b0e5-4127-85e1-745cb500d6b8 /media/Downloads       ext3    defaults        0       2
```

Try that first to get the partition to mount in the first place, and then start changing the options to your needs.

Anyway, your problem is simply that something in your fstab entry is not correct, which prevents the partition from being mounted at that time. It then gets automounted (using the label) at later time, but the new name still appears in Nautilus because the actual directory with that name exists in /media. As soon as you get the fstab entry to work correctly the drive wll be mounted using fstab instead of automounting it.

---

### Post by skaramanger on 2010-05-16
Kio_http, thanks for you reply.

Sorry but that folder is empty to begin with. Nothing to delete.

---

### Post by skaramanger on 2010-05-16
mcduck,

Is what is incorrect that I changed the mount point to /media/Download and replaced /MyDownloads in fstab?  Should I remove the parameter auto from fstab?  That turns off automounting right?

Thanks for your reply,

---

### Post by drs305 on 2010-05-16
You can change the partition label from Dnloads to Downloads with any of these methods:

Via Gparted (System, Admin, Gparted)
Via Disk Utility (System, Administration, Disk Utility)
Via command line:
```
sudo tune2fs -L Downloads /dev/sda7
```

Your title mentions changing the UUID label. More accurately, you would change the *partition* label. If you want to change the UUID, which isn't necessary in this case since you don't have duplicate UUIDs, you can use *tune2fs* to do that as well. See "man tune2fs".

If you make any changes in fstab, you can check to see if they work by closing open apps and running the following. System partitions will show busy, but others should unmount and then mount again.
```
sudo umount -a && sudo mount -a
```
or 
```
sudo umount /dev/sda7  && sudo mount /dev/sda7
```

---

### Post by skaramanger on 2010-05-16
Thanks DRS305 that did the trick!

---

### Post by skaramanger on 2010-05-16
Well I spoke too soon.  Using tune2fs -L <New Label> did change the name of the label, but did not actually 'fix' the problem.  I then just commented out the offending line in fstab and this removed duplication in nautilus.  However, I now have to mount it manually and I get prompt for a password when I click on Downloads in the nautilus left pane of available folders window.  I also removed the /media/Downloads folder. Automount was mounting the filesystem under /media/Downloads_. So I would tentatively called it remedied but not solved.  Still open to suggestions as to how to proceed from here.  My objective is to have it mount automatically w/o me have to tickle a keyboard or click an icon.

Thanks

---

### Post by drs305 on 2010-05-16
Do you have anything listed in your fstab for the partition? Make sure there isn't any other reference to Downloads or the partition - either by UUID or label. If not, try adding this. You will have to recreate your /media/Downloads folder. Make yourself the owner of the folder.

> LABEL=Downloads /media/Downloads defaults 0 2

---

### Post by John Bean on 2010-05-16
I think your manual settings in fstab are "fighting" with those used by FUSE to automatically mount external media. FUSE will attempt to create a new folder in /media with the same name as the disk label, and if it already exists will append an underscore to it, which is what you were seeing.

My suggestion is to mount the disk in /mnt rather than /media and add an appropriate entry in fstab. FUSE will then ignore the disk and it won't appear in "Places".

---

### Post by skaramanger on 2010-05-20
drs,

> **drs305 said:**
> Do you have anything listed in your fstab for the partition? Make sure there isn't any other reference to Downloads or the partition - either by UUID or label. If not, try adding this. You will have to recreate your /media/Downloads folder. Make yourself the owner of the folder.


Thanks, I'll try this when time permits.  Will post back with results.

---

### Post by skaramanger on 2010-05-20
John Bean,

> **John Bean said:**
> I think your manual settings in fstab are "fighting" with those used by FUSE to automatically mount external media. FUSE will attempt to create a new folder in /media with the same name as the disk label, and if it already exists will append an underscore to it, which is what you were seeing.


My suggestion is to mount the disk in /mnt rather than /media and add an appropriate entry in fstab. FUSE will then ignore the disk and it won't appear in "Places".

I didn't know what handled the automounting of filesystems. I'll look into it more. I'll consider mounting it there when I have more time to make changes.

Thanks for your reply

---

### Post by skaramanger on 2010-05-21
drs,

I made that change and after a reboot or two. I don't remember, I shut it down at night, but I now get only one entry for Downloads in nautilus and of course its icon displays on my desktop.

Thanks again

> **drs305 said:**
> Do you have anything listed in your fstab for the partition? Make sure there isn't any other reference to Downloads or the partition - either by UUID or label. If not, try adding this. You will have to recreate your /media/Downloads folder. Make yourself the owner of the folder.

---

