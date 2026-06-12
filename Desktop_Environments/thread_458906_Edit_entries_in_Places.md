---
title: "Edit entries in Places?"
date: 2007-05-30
forum: Desktop Environments
---

### Post by Blender on 2007-05-30
Hello!

I am having a minor, yet annoying problem.
I recently installed Feisty from the alternate CD (LVM system). At the intsallation, I was
being stupid and selected the option "Don't mount" (or so) for my NTFS partition, i.e. I
told the installer "yeah, I do have this partition and I do want to use it, but don't
mount it automatically". There was another option (well, something like "don't ever
use" or so :) ), which I should have chosen instead.

So, now that NTFS partition is in my Places menu and bar and I want to get rid of it,
because I rarely use that partition and mount it by hand.

The question: how do I "edit" those entries? I tried grepping **/etc**, but didn't find
anything. Is it possible to remove the "Network servers", too?

---

### Post by mcduck on 2007-05-30
For the NTFS partition, just remove it's entry from /etc/fstab, and then the actual directory from /media/.

I don't think you can get rid of the "Network Servers".

---

### Post by mlind on 2007-05-30
alternatively, if you have this partition defined in your /etc/fstab, use **noauto** option for it. This works at least with the ntfs kernel drivers, not sure if ntfs-3g supports this.
This way partition is not mounted automatically on boot, but you can still mount it using the fstab entry.

---

### Post by Blender on 2007-05-30
Thanks for the replies, guys!

I am not a newbie ;) I don't have an entry in **/etc/fstab**.
Here's my file:
```


proc            /proc           proc    defaults        0       0
/dev/mapper/system-root /               ext3    noatime,user_xattr,errors=remount-ro 0       1
# /dev/sda2
UUID=508589ee-44c8-4080-a096-c7a8f5bb39a7 /boot           ext3    noatime         0       2
/dev/mapper/system-home /home           ext3    noatime,user_xattr 0       2
# /dev/sda3
UUID=314ac867-e0d4-443d-a833-88f4eb9281c9 none            swap    sw              0       0

```

In fact, since the installation of Feisty, I haven't ever mounted that partition.

---

### Post by mcduck on 2007-05-30
Then check if you still have the directory in /media. Or check if it's still in your Nautilus bookmarks (Places/Edit Bookmarks in spatial mode and Bookmarks/Edit Bookmarks in browser mode).

---

### Post by mlind on 2007-05-30
seems like hal -> gnome-mount is doing the job automatically for you. I guess you can use a fstab entry for the partition and "auto mounters" should leave it alone.


Here's an example from my /etc/fstab where I define one of my ntfs partitions as /media/C, but leave it umounted. I can later mount this by using "sudo mount /media/C". This entry doesn't appear in Places -menu. I'm using the kernel ntfs driver.
```

UUID=4234A9D134A9C7ED   /media/C        ntfs    defaults,**noauto**,ro,nls=utf8,umask=0007,gid=46   0       1

```
You need to adjust the UUID (use /sbin/vol_id for this) for your partition, and maybe remove the gid=46. I'm mounting the partition as root.plugdev, so only root and plugdev members have the access.

---

### Post by Blender on 2007-05-30
Thanks again :)

> **mcduck said:**
> Then check if you still have the directory in /media. Or check if it's still in your Nautilus bookmarks (Places/Edit Bookmarks in spatial mode and Bookmarks/Edit Bookmarks in browser mode).

The NTFS partition is not really a bookmark, i.e. you can't edit it (same as Home, Desktop, File System, etc.).

@mlind
Tried that, it still appears in Places. 
```

/dev/sda1       /mnt/windows    ntfs defaults,noauto,noexec,nosuid,nodev,ro,nls=utf8,umask=0007,gid=46          0 0

```

As I said, this is all because of that option I chose in the (debian) installer. 

I just grepped **/etc** for "ntfs", the UUID, the device name... nothing :(

I noticed something interesting, however. Now that I have a line in **/etc/fstab** for that partition, HAL picks the line (according to hal-device-manager) so that it is used when mounting the partition through HAL.

The only thing I can think of, is to "blacklist" that partition, at the HAL-level.

---

### Post by mlind on 2007-05-30
Try using mount point below /media instead. Ubuntu hal contains some hardcoded stuff related to mountpoints under /media.
Does your /etc/hal/fdi/policy/preferences.fdi contain anything related to this, excluding the entries which are commented out.

If your partition is visible in Places menu, but partition is not mounted I reckon it's a bug.

---

### Post by Blender on 2007-05-30
I created a directory under **/media**, set this dir to be the mount point and 
restarted... nothing...

I don't really think it's a bug, quite the opposite, because the options at the installer
were:
[list]
[*] Don't mount (but use, i.e. display it, so I can mount it)
[*] Don't use it at all (don't display it)
[/list]

Unfortunately I don't remember the exact wording.

I wanted to avoid this, but... I am gonna install Feisty *twice* in a VM and then compare 
the disks :(

---

### Post by Blender on 2007-06-01
OK, I installed Ubuntu in a VM and chose "Do not use partition". Booted... same thing. 
I guess HAL finds the partition and GNOME just picks up that information from HAL.

The only option left seems to be blacklisting the partition at the HAL level.

Thanks for the help!

---

### Post by mlind on 2007-06-01
> **Blender said:**
> OK, I installed Ubuntu in a VM and chose "Do not use partition". Booted... same thing. 
I guess HAL finds the partition and GNOME just picks up that information from HAL.

The only option left seems to be blacklisting the partition at the HAL level.

Thanks for the help!

That's weird because I have 3 ntfs partitions, which all are mounted under /media and only two of then show up in Places menu. The one I've defined with noauto using ntfs kernel driver doesn't show up unless I mount it manually.

Is your partition in a external hdd?

---

### Post by Blender on 2007-06-01
Do your partitions also show up in Computer or the places panel in Open/Save dialogs?

---

### Post by mlind on 2007-06-01
> **Blender said:**
> Do your partitions also show up in Computer or the places panel in Open/Save dialogs?

yes. The icon for non-mounted partition(s) looks different though.

---

