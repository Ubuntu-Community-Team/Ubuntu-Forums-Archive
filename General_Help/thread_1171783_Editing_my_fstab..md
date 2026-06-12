---
title: "Editing my fstab."
date: 2009-05-27
forum: General Help
---

### Post by Crafty Kisses on 2009-05-27
Hey guys I bought a Raptor 300G HD today, and every time I try to drag a file it says "Permission Denied" so I think I need to add it to my fstab, so I need some help, or if you guys have any other ideas that would be great! Here's some info on my setup:
[B]
sudo fdisk -l && sudo fdisk -lu[/B]

```
Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00098dd2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       36481   293033601   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2527a2c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *       10200       25497   122881185   83  Linux
/dev/sdb2           25498       60801   283579380    5  Extended
/dev/sdb5           59421       60801    11092851   82  Linux swap / Solaris
/dev/sdb6           44124       58793   117836712   83  Linux
/dev/sdb7           58794       59420     5036346   82  Linux swap / Solaris
/dev/sdb8           44102       44123      176683+  82  Linux swap / Solaris
/dev/sdb9           25498       43339   143315802   83  Linux
/dev/sdb10          43340       44101     6120733+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00098dd2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   586067264   293033601   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2527a2c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *   163846935   409609304   122881185   83  Linux
/dev/sdb2       409609305   976768064   283579380    5  Extended
/dev/sdb5       954582363   976768064    11092851   82  Linux swap / Solaris
/dev/sdb6       708836121   944509544   117836712   83  Linux
/dev/sdb7       944509608   954582299     5036346   82  Linux swap / Solaris
/dev/sdb8       708482628   708835994      176683+  82  Linux swap / Solaris
/dev/sdb9       409609431   696241034   143315802   83  Linux
/dev/sdb10      696241098   708482564     6120733+  82  Linux swap / Solaris

Partition table entries are not in disk order
```
Here is my current fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=1da3be08-29c4-4502-bd94-3146af5e0236 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=b9b7569c-3de1-4b58-be5d-d35ff421aba1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by logos34 on 2009-05-27
[Here ]("http://www.psychocats.net/ubuntu/mountlinux")you go

walks you through creating mountpoint, editing fstab and setting ownership+permissions

(*bottom->chown and chmod)

---

### Post by Crafty Kisses on 2009-05-27
Well here's a new problem that has arised, I have edited my fstab properly, I added the following to my **fstab**:
```
#
#/dev/sdb1
#
UUID=255872ef-8939-49de-a6db-fad364bb48ac /home/codename/Raptor     ext3    relatime        0       2
```
Now that I did that, I can mount the Raptor by running:
```
sudo mount /home/codename/Raptor
```
Then unmount the Raptor by running:
```
sudo umount /home/codename/Raptor
```
Then when I try to umount/mount via the GUI, I always get "Permission denied, must be root to mount "Raptor" or something to that extent. Any ideas? I've **chmoded to 755** and I've ran** chown**. I'm stuck. For those of you interested, here is my new **fstab**:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=1da3be08-29c4-4502-bd94-3146af5e0236 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=b9b7569c-3de1-4b58-be5d-d35ff421aba1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#
#/dev/sdb1
#
UUID=255872ef-8939-49de-a6db-fad364bb48ac /home/codename/Raptor     ext3    relatime        0       2
```

---

### Post by Crafty Kisses on 2009-05-27
Alright still no luck guys, I've done everything to my knowledge to get this to work and it's still not working. So here are the results of **sudo blkid**:
```
/dev/sdb1: LABEL="Extra Space" UUID="9c3dee66-dd78-448e-ad44-32b04440e538" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="8c7fd7c1-26b3-427a-8c5b-69298720b7ca" 
/dev/sdb6: UUID="1da3be08-29c4-4502-bd94-3146af5e0236" TYPE="ext3" 
/dev/sdb7: TYPE="swap" UUID="b9b7569c-3de1-4b58-be5d-d35ff421aba1" 
/dev/sdb8: TYPE="swap" UUID="d7141acd-5535-4141-aaf4-7b400de78796" 
/dev/sdb9: LABEL="Kubuntu" UUID="45c6e9d1-5310-4da4-a0a0-29f13504b6cd" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb10: TYPE="swap" UUID="97b023d3-e4d3-427a-befe-03901bd303d5" 
/dev/sda1: L**ABEL="Raptor" UUID="255872ef-8939-49de-a6db-fad364bb48ac" SEC_TYPE="ext2" TYPE="ext3"** 
codename@codename
```
Now I'm not sure if you have to reboot once you've edited your fstab, which I've done a lot now, but here is my current fstab as of now:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=1da3be08-29c4-4502-bd94-3146af5e0236 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=b9b7569c-3de1-4b58-be5d-d35ff421aba1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#
#/dev/sdb1                           rw,user,auto, 0 0
#
UUID=255872ef-8939-49de-a6db-fad364bb48ac /home/codename/Raptor     ext3    relatime    0       0
```
If you have noticed, I've added the following in the fstab:
```
rw,user,auto 0 0
```
Once I added those lines in my fstab, I ran the following:
```
sudo mount -a
```
Then I right clicked on my drive, and clicked "Mount" then I get the following error message:
```
You are not privileged to mount the volume 'Raptor'.
```
Then as I've stated already I can mount/unmount via the Terminal, if I run:
```
sudo mount /home/codename/Raptor
```
It will mount and if I run:
```
sudo umount /home/codename/Raptor
```
It will obviously unmount, the real issue here is I think it's not auto mounting for whatever reason, if anyone wants to edit my fstab feel free to, I think I have it right but if I don't please correct me.

---

### Post by logos34 on 2009-05-27
maybe having a mount point inside /home is causing problems...Try using default /media dir

sudo mkdir /media/raptor

chmod and chown it

I'd either use 'defaults' or 'relatime' options only in fstab.  Doublecheck the UUID:

sudo vol_id -u /dev/sda1

ls -l /dev/disk/by-uuid

> # /dev/sda1
UUID=255872ef-8939-49de-a6db-fad364bb48ac /media/raptor ext3 defaults 0 2

does it automount on boot?

---

### Post by Crafty Kisses on 2009-05-27
Yeah it does, I just rebooted and it was already mounted. I just can't mount/unmount it via the GUI which is weird.

---

### Post by Boondoklife on 2009-05-27
> **Codename said:**
> Yeah it does, I just rebooted and it was already mounted. I just can't mount/unmount it via the GUI which is weird.

Hmm I was under the impression that this is normal, I have a seperate partition and I have amount and need sudo to mount/unmount kinda like a cifs share.

---

### Post by Crafty Kisses on 2009-05-27
Well it's not a big deal really, I did what you asked logos, here is my new fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=1da3be08-29c4-4502-bd94-3146af5e0236 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=b9b7569c-3de1-4b58-be5d-d35ff421aba1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#
#/dev/sda1                          
#
UUID=255872ef-8939-49de-a6db-fad364bb48ac /media/raptor     ext3    defaults    0       2
```
I still have to do it via command line, but it's not that big of a deal. That's weird though. It's also still auto mounting.

---

### Post by logos34 on 2009-05-28
yeah, malatek is right, it's normal...you have to mount/umount drive manually from cli...I misinterpreted post #4 to mean you were just having trouble getting it mounted at boot...(I'm distracted by my own problems getting custom Mmplayer compiled!)

---

### Post by dmizer on 2009-05-28
Per man mount:
```
              defaults
                     Use  default  options: rw, suid, dev, exec, auto, [COLOR="Red"]nouser[/COLOR],
                     and async.
```
```
              [COLOR="Red"]nouser[/COLOR] Forbid  an  ordinary  (i.e.,  non-root) user to mount the
                     file system.  This is the default.
```
Don't reboot before making sure this works.

Unumount the disk: sudo umount /media/raptor
Change the fstab options like so:
```
UUID=255872ef-8939-49de-a6db-fad364bb48ac /media/raptor     ext3    users,rw,dev,exec,suid,async    0       2
```
Then try to mount it as yourself:
```
mount /media/raptor
```

If it doesn't work, return /etc/fstab to its original state.

---

### Post by Crafty Kisses on 2009-05-31
Hey there dmizer! I finally added the following to my fstab:
```
  defaults
                     Use  default  options: rw, suid, dev, exec, auto, nouser,
                     and async.
```
Then when I run the following:
```
mount /media/raptor
```
It actually works, but it still won't let me unmount for some reason, but that's good enough. Thanks for all the help. ;-)

---

### Post by dmizer on 2009-05-31
It should work both ways. What's your current /etc/fstab line?

---

### Post by Crafty Kisses on 2009-06-03
Here is my current fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=1da3be08-29c4-4502-bd94-3146af5e0236 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=b9b7569c-3de1-4b58-be5d-d35ff421aba1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660, rw, suid, dev, exec, auto, nouser, async, utf8 0       0
#
#/dev/sda1                          
#
UUID=255872ef-8939-49de-a6db-fad364bb48ac /media/raptor     ext3    defaults    0       2
```
Like I've stated it just wont unmount and like you've said it should work both ways, but I'm just not sure why it isn't. It isn't all that big of a deal, I really don't mind mounting the drive via the CLI.

---

### Post by sehe on 2009-06-03
don't use nouser, use -o user or 'user' option in fstab

other idea: 'adduser username disk' and relogin

---

### Post by dmizer on 2009-06-03
Your fstab looks really messed up.

Make a backup of it:
```
sudo cp /etc/fstab /etc/fstab-old
```
And replace it with this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=1da3be08-29c4-4502-bd94-3146af5e0236 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=b9b7569c-3de1-4b58-be5d-d35ff421aba1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0  udf,iso9660 user,noauto     0       0

# Mount line for raptor drive
UUID=255872ef-8939-49de-a6db-fad364bb48ac /media/raptor      ext3    users,noauto,rw,dev,exec,suid,async    0       2
```

---

### Post by Crafty Kisses on 2009-06-05
So finally I replaced the fstab with:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=1da3be08-29c4-4502-bd94-3146af5e0236 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=b9b7569c-3de1-4b58-be5d-d35ff421aba1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0  udf,iso9660 user,noauto     0       0

# /media/raptor
UUID=255872ef-8939-49de-a6db-fad364bb48ac /media/raptor      ext3    users,noauto,rw,dev,exec,suid,async    0       2
```
To no avail, it doesn't work, but again I can mount/unmount the HD as stated in this thread already by running:
```
sudo mount /media/raptor
sudo umount /media/raptor
```
I also tried what sehe suggested which was adding:
```
adduser username disk
``` And after that I unmounted my Raptor drive, and ran:
```
sudo mount -a
```
Then again I tried to unmount it via the GUI, and still nothing. Now from my understanding by adding:
```
user
```
Under the list of options in fstab any user should be able to mount the drive without root privledges. Then it automatically assumes you also have:
```
nosuid
nodev
```
So in theory this should actually be working right now, I've also restarted by running:
```
sudo shutdown -r now
```
I'm just not seeing results. It doesn't really matter to me, I don't mind mounting the drive via the CLI I guess. Thanks for all the help guys.

---

### Post by Crafty Kisses on 2009-06-05
Double post, I'm sorry.

---

