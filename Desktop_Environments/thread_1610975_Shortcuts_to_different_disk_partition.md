---
title: "Shortcuts to different disk partition"
date: 2010-11-01
forum: Desktop Environments
---

### Post by laurimyllyvirta on 2010-11-01
Hi,

I installed Lucid Lynx on a HD that already hosted WinXP, creating a new partition for Ubuntu. My documents are on the old partition. The problem is, every time I reboot, all my shortcuts to the Win partition break - I would like to have a shortcut to my Win desktop on my Ubuntu desktop, have links to Win programs I run with Wine etc.

Ubuntu calls the WinXP partition "230 GB Filesystem" and mounts it under /media/ with a funny folder name that looks like a long hex number. I guess the shortcuts break because the hex number changes. Ubuntu does not let me rename the partition into something more intelligible.

(Ideally, I would like my WinXP and Ubuntu to share the same desktop, the one on the WinXP partition, is this possible?)

Could not find overlapping threads, feel free to point me to them if there are any I missed.

Thanks!

---

### Post by Naitsirhc Hsem on 2010-11-01
It is definitly possible.  I do not know the exact method but look into modifying /etc/fstab from the forums.  this will allow mount at boot. you can specify a specific place and name for mounting.

cheers

---

### Post by oldfred on 2010-11-01
One quick way to consistency is to use System, Administation, Disk Utility and assign a label to your partition.  You then should see it as the label and not some general id.

But the best way is to permanently mount it. But I do not recommend writing into the windows system partition as you can corrupt the windows by accident. I prefer a separate shared NTFS partition.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by laurimyllyvirta on 2010-11-03
Thanks! I tried a few programs and got it sorted out using mountmanager, after setting a permanent mount location for the partition the links are not breaking anymore.

oldfred, I will create a new partition as you suggest, wasnt aware of the risk of corrupting WinXP.

Does anyone know a way to define the path to your desktop as something else than home/username/Desktop/?

---

### Post by corncob on 2010-11-03
> **laurimyllyvirta said:**
> 
Does anyone know a way to define the path to your desktop as something else than home/username/Desktop/?

~/Desktop/ ?

---

### Post by oldfred on 2010-11-03
You can mount the NTFS partiiton anywhere. I mount mine into /shared in my home. 

```
# Entry for /dev/sdc2 :
UUID=44332FD360AA9657                      /home/fred/shared  ntfs-3g      defaults                             0  0  
```

You also can mount it anywhere and link folders into /home. I do that with my /data (ext3) partiton which has all the standard default folders, like Documents, Downloads, etc.

Details:
man ln

I believe something like this would work, you have to delete or rename the current folder (make sure it has no data):
If mounted as /data or in root of entire system.

ln -s /data/Music

If run from your home, the default location of the link is where you run it from, so the link goes into /home/fred in my case.

---

