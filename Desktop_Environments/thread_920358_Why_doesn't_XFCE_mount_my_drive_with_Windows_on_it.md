---
title: "Why doesn't XFCE mount my drive with Windows on it, but Gnome does in Hardy?"
date: 2008-09-15
forum: Desktop Environments
---

### Post by boomtisk on 2008-09-15
This is pretty weird, I'm a big fan of XFCE but for some reason my "Windows drive" (I have two HDs installed, one with Linux and the other one with Windows XP on it) fails to mount when I use it. Why should two desktop environments handle mounting differently? The drive works fine in Gnome and can be accessed with the "Places" menu, but I don't really like Gnome all that much.

Here's my /etc/fstab, I modified the sda1 section a bit (that's my master HD with Windows on it) a bit to match the sdb entry (my "Linux drive") but it didn't do anything. 

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=a45c293a-cf70-4451-aacd-de48472430c9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=ed1f6418-74b6-48f4-8482-e3f8c918313e none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

# /dev/sda1
UUID=305821F55821BA8C                     /media/sda1     ntfs    relatime,errors=remount-ro 0       1
```

I use Ubuntu Studio Hardy with the repo version of XFCE installed on top of it. Any advice? Lots of thanks in advance.

---

### Post by prshah on 2008-09-15
> **boomtisk said:**
> 
```

# /dev/sda1
UUID=305821F55821BA8C                     /media/sda1     ntfs    relatime,errors=remount-ro 0       1
```


First of all, playing with fstab without proper knowledge will lead to all kinds of grief. For proper understanding of the fstab, use the command ```
man fstab
```

As an example, specific to this case, you cannot (re)mount an NTFS filesystem with errors.

If you still have access to your (other) linux distro, get the correct fstab options from that, otherwise, the below should serve as a guideline```
# /dev/sda1
UUID=688C-A6A1  /media/sda1     ntfs    defaults,umask=007,gid=46 0       1

```

1) Check the UUIDs match; use the command ```
sudo blkid /dev/sda1
``` to find the UUID, and compare it to the one listed in the fstab.

2) In the options, include "defaults" (there is no "relatime" settings for ntfs), and, if you include the gid setting as above, change it to whatever your plugdev group's gid is (it usually should be the same).

3) Ensure your user is a member of group plugdev (Usually all users are also members of plugdev by default).

Post back if you need more specific pointers.

---

### Post by boomtisk on 2008-09-15
Hi, yeah, I guess I was kind of a big idiot for playing around with the command like that, and I guess my tremendous laziness prevented me from reading the manpage.

Anyway, thanks to your advice, I got the drive to automount; it still didn't show up in my Places menu like it does in Gnome, so I just bookmarked the folder in /media/. It's still kind of weird that this is happening (I don't recall having this problem in Gutsy) but at least I can access the drive in XFCE now. Thanks a lot!

---

### Post by navinmistry on 2009-05-09
i installed XFCE over my UBUNTU and i had the same problem that it was not automounting the windows partition.

however my gnome in ubuntu does using ntfs-3g command (internally)

i have added my partition in fstab entry which now looks like:

/dev/sda2     /media/SYSTEM    ntfs-3g    rw,nosuid,nodev,allow_other    0    0
/dev/sda5     /media/DATA    ntfs-3g    rw,nosuid,nodev,allow_other     0       0
/dev/sda6     /media/ENTERTAINMENT    ntfs-3g    rw,nosuid,nodev,allow_other     0       0


u can check your partition number using partition editor.
u must need to create the directories as i did ( /media/<UR_PARTITION NAME).

upon next login, i am getting my partition are visible to me..

good luck .
Navin Mistry.

---

