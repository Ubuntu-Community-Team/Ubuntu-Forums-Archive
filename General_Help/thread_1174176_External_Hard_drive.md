---
title: "External Hard drive"
date: 2009-05-30
forum: General Help
---

### Post by Betraythesway on 2009-05-30
Hi I just recently transitioned over from a windows system to Ubuntu and I seem to be having a problem mounting my external hard drive. when ever I plug in my hard drive a window pops up and it tells me 

"Invalid mount option when attempting to mount the volume 'My Book'. 

shortly after that I get a second message which tells me

 "DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

I am very new to the OS and so this problem is very troublesome could someone please help?

---

### Post by drs305 on 2009-05-30
Welcome to the ubuntu forums!

Did you try to add an entry to fstab or run NTFS Configuration Tool? 

Please post the results of:
```

sudo fdisk -l  # small L
cat /etc/fstab  # if you ran the NTFS config tool or edited fstab

```

---

### Post by Betraythesway on 2009-05-30
Ok I got

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbae9bae9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23566   189293863+  83  Linux
/dev/sda2           23567       24321     6064537+   5  Extended
/dev/sda5           23567       24321     6064506   82  Linux swap / Solaris

and

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=849a6a71-2998-407e-a66c-d1608eb539e7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ce71429e-f5f3-43bc-a27a-9ba46b682f74 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

I did try to edit fstab after the problem started but to no avail.

---

### Post by kmitnick on 2009-05-30
are you running it while the External HDD is connected?
and btw run this in terminal 
```
ls /dev | grep sd
```

---

### Post by Betraythesway on 2009-05-30
Oh sorry I did unplug it I'm such a dunce. I ran the line you kmitnick and it once again gave me could not mount and this:

ptysd
sda
sda1
sda2
sda5
sdb
sdc
sdd
sde
sdf
sdg
sdg1
ttysd

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbae9bae9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23566   189293863+  83  Linux
/dev/sda2           23567       24321     6064537+   5  Extended
/dev/sda5           23567       24321     6064506   82  Linux swap / Solaris

Disk /dev/sdg: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       19457   156288321    c  W95 FAT32 (LBA)

And 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=849a6a71-2998-407e-a66c-d1608eb539e7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ce71429e-f5f3-43bc-a27a-9ba46b682f74 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by drs305 on 2009-05-30
As kmitnick suggested, the external drive must be connected and powered up. Right now the system is not seeing the external drive at all. When it does, you will see an extra entry with the fdisk command - probably "sdb" and "sdb1" with a format of HPFS/NTFS.

It should automount without any entry in fstab =- adding the entry in fstab just gives you some control over where and how it is mounted.
[B]
Added:[/B]
Try doing this. Create a new mount point and try manually mounting the device:
```

sudo mkdir /media/test
sudo mount /dev/sdg1 -t vfat /media/test

```

---

### Post by Betraythesway on 2009-05-30
Yeah I'm sorry about that but it was connected the last time i ran the commands you gave me in my last post.

---

### Post by Betraythesway on 2009-05-30
Ok so I ran the lines you suggested in your last post drs305 and it did mount, so how can I get it to auto mount when I plug it in?

---

### Post by kmitnick on 2009-05-30
in the /etc/fstab add this line
> /dev/sdg1   /media/test    vfat    user,auto    0    0

---

### Post by kmitnick on 2009-05-30
and then try ```
 mount -a
```

---

### Post by Betraythesway on 2009-05-30
Ok so I added the line to fstab and then ran mount -a

I unplugged the drive and plugged it back in and it gave me the same line bout not being able to mount My Book. Sorry I feel like a pain.

Oh, and now I can't even mount it manually.

---

### Post by drs305 on 2009-05-30
Does the mount point /media/test mentioned now in fstab exist? If not, you need to make it. The second command makes you the owner of /media/test, although this isn't necessary when it comes to vfat mounts:
```
sudo mkdir /media/test
sudo chown -R [COLOR="DarkRed"]*yourusername*[/COLOR]: /media/*[COLOR="DarkRed"]test[/COLOR]* 

```

These drives can be tricky. If it has both a power cord and a usb input try powering it up first, then plugging in the usb device. If that doesn't work, reverse the process. 

Try changing the fstab entry to the following. It assumes you are user 1000. You can check this with "id" in terminal. 
> 
/dev/sdg1 /media/*[COLOR="DarkRed"]test[/COLOR]* vfat auto,users,uid=*[COLOR="DarkRed"]1000[/COLOR]*,utf8,umask=027 0 0


You might want to make a label for the external. The easiest way to do this for a vfat filesystem is to open gparted (gksudo gparted), highlight the device, right click and select "Label".

If it works, I would tweak the fstab entry to use either a label or a UUID since it's an external drive and the "sdg" designation could possibly change. We can help you there once you get the bigger problem solved.

Here is a link to explain the fstab entries:
[http://ubuntuforums.org/showthread.php?&t=283131]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by Betraythesway on 2009-05-30
Wow thanks i have it auto mounting again but it is giving me a different sort of problem now. For some reason all of my file permissions are messed up and it will not let me change them. When I open properties then permissions I have folder access to read and write but no permissions on the files I try to change this but for some reason am unable too. I was not having this problem before the whole mounting problem happened what is going on?

---

### Post by drs305 on 2009-05-30
> **Betraythesway said:**
> Wow thanks i have it auto mounting again but it is giving me a different sort of problem now. For some reason all of my file permissions are messed up and it will not let me change them. When I open properties then permissions I have folder access to read and write but no permissions on the files I try to change this but for some reason am unable too. I was not having this problem before the whole mounting problem happened what is going on?

Permissions for non-linux file systems are set at the time of mounting. You can read/write them as you see, but the folder will be owned by root, since non-native file systems don't support linux permissions. The permissions are set at the time of mounting and cannot be changed. 

Are you user 1000? Are you using the fstab line I suggested in the previous post? Let's simplify the fstab entry to:
```

/dev/sdg1 /media/test vfat defaults,users,uid=1000,utf8,umask=000 0 0 

```

---

### Post by Betraythesway on 2009-05-30
I checked my id yes I am use 1000 and my fstab reads exactly as such:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=849a6a71-2998-407e-a66c-d1608eb539e7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ce71429e-f5f3-43bc-a27a-9ba46b682f74 none            swap    sw              0       0
/dev/sdc1 /media/test vfat auto,users,uid=1000,utf8,umask=000 0 0 

Like I said it is mounting just fine but still no luck with the permission.

---

### Post by drs305 on 2009-05-30
It was originally sd**g** according to fdisk. In the fstab you posted it is sd**c**. Typo or a change?

It certainly *can* change, which is why I would change /dev/sdXX to a label or UUID once everything is fixed.

---

### Post by Betraythesway on 2009-05-30
Yeah apparently it changes this is what it has in the log now.

[FONT=monospace]Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbae9bae9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23566   189293863+  83  Linux
/dev/sda2           23567       24321     6064537+   5  Extended
/dev/sda5           23567       24321     6064506   82  Linux swap / Solaris

Disk /dev/sdh: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1       19457   156288321    c  W95 FAT32 (LBA)
[/FONT]

---

### Post by drs305 on 2009-05-30
It's time to implement something I suggested we do later. Since it's changed twice already, I suggest you replace the device designation (sdXX) in fstab with the UUID.

To get the UUID, run this:
```

sudo blkid

```
Note the UUID of sdh1 (or whatever it's calling itself now), and change the start of the fstab line as in this example. Change the UUID to the one from the command you ran:
```

*From:*
/dev/sdh1  /media/test .......
*To:*
UUID=[COLOR="DarkRed"]269d31ae-24c9-451a-a71b-8224e35516[/COLOR]  /media/test .......

```

This will ensure fstab always correctly identifies the external partition.

---

### Post by Betraythesway on 2009-05-30
Ok so this is what I came up with 

/dev/sda1: UUID="849a6a71-2998-407e-a66c-d1608eb539e7" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="ce71429e-f5f3-43bc-a27a-9ba46b682f74" 
/dev/sdh1: LABEL="My Book" UUID="3717-D230" TYPE="vfat" 
 
and so I changed my fstab to look like this now.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=849a6a71-2998-407e-a66c-d1608eb539e7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ce71429e-f5f3-43bc-a27a-9ba46b682f74 none            swap    sw              0       0
UUID="3717-D230" /media/test vfat auto,users,uid=1000,utf8,umask=000 0 0

---

### Post by drs305 on 2009-05-30
> **Betraythesway said:**
> Ok so this is what I came up with 
UUID="3717-D230" /media/test vfat auto,users,uid=1000,utf8,umask=000 0 0

Close but not quite - no quotes. While we are changing it, let's change  the rest of the line a bit:

> 
UUID=3717-D230 /media/test vfat defaults,users,uid=1000,utf8,umask=000 0 0


Tip: Spaces in partition labels can also be a bit problematic. You can change the label "My Book" to something of your choosing by opening gparted ("gksudo gparted" or System, Administration, Partition Editor). Highlight the appropriate partition, right click, Label, and enter a new label name, preferably with no spaces in the name.

Also, since nobody has mentioned it in this thread, the fastest way to check if the fstab setting will work is with:
```

sudo umount /dev/sd**h1**  # or whatever the designation
sudo mount /dev/sd**h1**  #

*or more simply*:

sudo umount -a  # you may get a lot of 'busy' messages. Ignore them.
sudo mount -a


```

---

### Post by Betraythesway on 2009-05-30
Ok, I've got that but still not able to place anything on my hard drive. Whats the next step?

---

