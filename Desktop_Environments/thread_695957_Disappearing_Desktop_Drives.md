---
title: "Disappearing Desktop Drives"
date: 2008-02-13
forum: Desktop Environments
---

### Post by gt_momo on 2008-02-13
Up until this morning I had two NTFS drives on my desktop at each boot. Now they are missing.

I added these two lines to my fstab file and everything was working fine.

/dev/hda1	/mnt/ntfs-1	ntfs-3g	defaults	0	0
/dev/hdd2	/mnt/ntfs-2	ntfs-3g	defaults	0	0

But now the drives no longer appear in the Computer link in Nautilus or my desktop.

I can mount and unmount the drives as usual and access them as well but no icons.

---

### Post by taurus on 2008-02-13
What happens when you run this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo mount -t ntfs-3g /dev/hda1 /mnt/ntfs-1
```
I am sure you will be greeted with a message saying something like you didn't shut down your windows cleanly so you need to boot into windows and shut it down cleanly or you have to use the force option to mount it.

---

### Post by gt_momo on 2008-02-13
> **taurus said:**
> What happens when you run this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo mount -t ntfs-3g /dev/hda1 /mnt/ntfs-1
```
I am sure you will be greeted with a message saying something like you didn't shut down your windows cleanly so you need to boot into windows and shut it down cleanly or you have to use the force option to mount it.

Actually, nothing happens at all. It mounts it and I'm able to use it with no warnings or errors. In fact, I've not used Windows at all since this has occurred.

edit: Here's something. If I remove those lines from fstab and reboot the system, I'm once again able to see the drives as usual in the Computer link in Nautilus and when they're mounted I'm able to see the drive icons once again. However, upon restart they disappear.

---

### Post by taurus on 2008-02-13
Then I guess you can mount the other partition too.

```
sudo mount -t ntfs-3g /dev/hdd2 /mnt/ntfs-2
```
Now, can you post the outputs of these commands?

```
cat /etc/fstab
df -h
```

---

### Post by gt_momo on 2008-02-13
> **taurus said:**
> Then I guess you can mount the other partition too.

```
sudo mount -t ntfs-3g /dev/hdd2 /mnt/ntfs-2
```
Now, can you post the outputs of these commands?

```
cat /etc/fstab
df -h
```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=1a8c2a47-6042-4037-b02e-32bba5fff295 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=e2a2fc7b-afd0-466d-8323-e20907684bff none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

/dev/hda1	/mnt/ntfs-1	ntfs-3g	defaults	0	0
/dev/hdd2	/mnt/ntfs-2	ntfs-3g	defaults	0	0
```
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb1             144G  5.6G  131G   5% /
varrun                506M  204K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M  108K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/hda1             280G  156G  124G  56% /mnt/ntfs-1
/dev/hdd2             277G   27G  251G  10% /mnt/ntfs-2
```

Here's something. If I remove those lines from fstab and reboot the system, I'm once again able to see the drives as usual in the Computer link in Nautilus and when they're mounted I'm able to see the drive icons once again. However, upon restart they disappear if the fstab lines are renewed.

---

### Post by gt_momo on 2008-02-13
bump

---

### Post by gt_momo on 2008-02-14
:(

---

### Post by SonicSteve on 2008-02-18
I have the exact same trouble on all my Gutsy installations EDIT (my laptop doesn't suffer from this). It is definately either a very persistent bug, or it's by design in gutsy. I lean towards a bug. 

The mounts are all good, I can browse to the mount point and access the data that FSTAB has mounted. However they're not in the Places menu or in nautilus or on the desktop. It's quite annoying. I'm going to keep looking for answers.

I've taken to creating custom launchers on the desktop and then copying them to a panel. That way I still at least have quick access, I change the icon also since the default launcher Icon is less than exciting. The icons can be found in /usr/share/icons.

---

### Post by SonicSteve on 2008-02-18
OK I searched in Launchpad,
It appears to a very persistent bug. It happens in most of my Gutsy installations.

Remount your drives with mount points in the /media folder. Your's and mine were in the /mnt folder. After changing the FSTAB and adding the new folders in /media reboot. CTRL-ALT-BKSPC might also do it. 
My icons are back, for some reason only mounts made in the /media folder appear on the desktop and in Nautilus now. 

This link in Launchpad is for Hardy Alpha 3, apparently it applies to Gutsy also.
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/185463](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/185463)

---

### Post by gt_momo on 2008-02-18
Thank you very much for replying, Steve :)

Knowing that this bug should soon be fixed makes me happy.

---

### Post by SonicSteve on 2008-02-18
You're welcome,

Though the bug they experience is kind of the opposite of ours. We want drives mounted in /mnt to appear on the desktop and here is a quote from launchpad

> drives mounted under /mnt are appearing as icons on the desktop.

Only drives under /media should appear on the desktop.

It seems they are saying that in Hardy only a drive mounted in /media will show on the desktop and if a drive mounted in /mnt shows up its a bug.

It would be nice for someone to confirm this, that in Gutsy both mount folders show or are supposed to show up on the desktop. AND that in Hardy this behaviour has been changed so that only the /media folder show up on the desktop. Or is the information on launchpad incorrect.

---

