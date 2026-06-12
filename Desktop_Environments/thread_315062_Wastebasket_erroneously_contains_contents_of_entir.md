---
title: "Wastebasket erroneously contains contents of entire mounted partition!"
date: 2006-12-08
forum: Desktop Environments
---

### Post by pwhite on 2006-12-08
Edit: I can't explain, but I did a hard-shutdown (just turned off the power supply), and when it came back up everything was back to normal - go figure...




After messing with my external usb audio, I suddenly started having problems with my wastebasket. I'm not sure if this is completely coincidental, but I'm at a complete loss at how to resolve it...

The entire contents of my /dev/sdb1 partition appears in the Trash unless I mount it as read-only. I've remove ~/.Trash and ~/.nautilus, rebooted several times, undid the changes I made to my sound conf - nothing seems to work. This has me completely freaked out because anything I actually delete will be added to the trash bin and mixed in with the content from my 2nd hard so I'm afraid that emptying the trash will delete the entire contents of my 2nd drive...

The output from mount is:

/dev/sda1 on / type ext3 (rw,noatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
/dev/sda3 on /home type ext3 (rw,noatime,user_xattr,errors=remount-ro)
/dev/sda4 on /opt type ext3 (rw,noatime,errors=remount-ro)
/dev/sdb1 on /storage type ext3 (rw,noatime,errors=remount-ro)

My fstab entry for /storage is:

UUID=d5d4c841-a491-447f-894c-db45f61bdad5 /storage ext3 defaults,errors=remount-ro,noatime 0 1

As mentioned previously, adding "ro" as an option in fstab and remounting removes the contents of /storage from the Trash but I need to be able to write to this partition.

uname -a returns:

Linux zippy 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux

Any pointers in the right direction would be greatly appreciated!

Thanks,
Peter

---

### Post by blackstone on 2006-12-13
Hi

I'm experiencing the same problem. I mounted a new 250GB volume and all seemed to be fine until I rebooted, and now the entire volume is being seen as trash. If I empty my trash, everything on that volume is deleted!

Did you have any success in resolving this?

---

### Post by tszanon on 2006-12-13
Similar problem here. When I delete something, it's moved to ~/.Trash. But the trash can is always empty. if I click on it to show me the deleted files, it still shows me that it has no files. But they're there, I can see them through the Terminal...:-k

---

