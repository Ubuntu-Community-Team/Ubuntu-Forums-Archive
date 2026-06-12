---
title: "how to stop gnome-mount mounting a disk"
date: 2008-12-08
forum: Desktop Environments
---

### Post by ocalld on 2008-12-08
Hi
I'm running Ubuntu 8.10

I have a 3 disk stripe setup on a fake raid.
Unfortunately, gnome-mount tries to mount one of the disks  (only one not the three). it tries to mount /dev/sda instead of mapper device.

i have dmraid installed and the device is listed in /dev/mapper/.

i can't mount the stripe set as gnome-mount tries to mount the single disk first.
i believe this is done by "hal".

how can i stop hal / gnome-mount from trying to mount the disk??

thanks.
dan

---

### Post by psusi on 2008-12-08
Gnome does not auto mount non removable disks by default, did you maybe add that disk to your /etc/fstab?  If so, remove it.

---

### Post by ocalld on 2008-12-09
> **psusi said:**
> Gnome does not auto mount non removable disks by default, did you maybe add that disk to your /etc/fstab?  If so, remove it.

Hi

i can confirm, no entry exists in the fstab.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdd1
UUID=811c2590-e199-4719-9d75-e9f20c3d0f41 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdd5
UUID=95406257-a302-41fc-bb44-adb15cccce6d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


## stripe set
/dev/mapper/isw_bgfgbhheai_Volume01     /export/stripe0 ext3    defaults        0       0



The disk isn't actually mounted. I see an icon for it in "Computer" and i have to right mouse click for mount.

I believe it's what ever program produces the icon (hal i think) for the disk in "computer" is stopping me from mounting the stripe set in /dev/mapper.

Thanks
Dan

---

### Post by psusi on 2008-12-09
Can you post the output of sudo mount and blkid?

---

### Post by ocalld on 2008-12-09
> **psusi said:**
> Can you post the output of sudo mount and blkid?

Hi 
Thanks for the help.

sudo mount:
/dev/sdd1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-10-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/danielo/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=danielo)


sudo blkid:
/dev/sda1: UUID="07db36e5-4b44-4554-b66c-e007d2989e5d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdd1: UUID="811c2590-e199-4719-9d75-e9f20c3d0f41" TYPE="ext3" 
/dev/sdd5: TYPE="swap" UUID="95406257-a302-41fc-bb44-adb15cccce6d" 
/dev/mapper/isw_bgfgbhheai_Volume01: UUID="07db36e5-4b44-4554-b66c-e007d2989e5d" SEC_TYPE="ext2" TYPE="ext3"


Thanks
Dan

---

### Post by psusi on 2008-12-09
Hrm... well it should not be identifying sda with the UUID, but since your fstab is not using the UUID, it shouldn't really matter.  Try running sudo mount /export/stripe0.

Since you don't have it mounted in /media it will not show up in the places menu in gnome.  Out of curiosity, why did you want to mount it in /export?

Can you also post the output of sudo dmraid -n and sudo vol_id /dev/sda.

---

### Post by ocalld on 2008-12-09
> **psusi said:**
> Hrm... well it should not be identifying sda with the UUID, but since your fstab is not using the UUID, it shouldn't really matter.  Try running sudo mount /export/stripe0.

Since you don't have it mounted in /media it will not show up in the places menu in gnome.  Out of curiosity, why did you want to mount it in /export?

Can you also post the output of sudo dmraid -n and sudo vol_id /dev/sda.

Hi

Thanks for your help.
I've managed to fix it.
I booted to the live cd and installed dmraid.
I still couldn't mount the stripe, so basically that ruled out my Ubuntu install.

I tried gpart, that wouldn't load against the raid.

In the end i had to delete the raid from my bios and recreate it, Ubuntu now see everything perfectly.

The reason i mounted on /export was an old habit from working with Solaris.

Again, thanks for the help, i've learned a few new commands in the process.


Cheers
Dan.
:popcorn:

---

