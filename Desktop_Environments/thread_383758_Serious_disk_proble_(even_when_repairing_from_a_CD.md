---
title: "Serious disk proble (even when repairing from a CD)"
date: 2007-03-13
forum: Desktop Environments
---

### Post by EarlGrey on 2007-03-13
Hello,

I have run into a very strange and serious problem. Quite often now my system goes dead and if I switch into a console ctrl+alt+1, it gives me an error as follows. Similar thing happens even when I boot from a cd and run

sudo fsck.ext3 -p -c -f /dev/sda1

The error is always similar to:

[17179729.68400] ata1: translated stat/err 0x51 to SCI SK/ASC/ASCQ 0xb/00/00

Does anyone know what that could mean? The disk is two months old and I did not experience any problems in these two months.

---

### Post by daengbo on 2007-03-13
What kind of system are you running? Is that a real SCSI drive or something emulated? Please give as much information as possible, including a cat of /proc/mounts and the output of uname -a.

Thanks

---

### Post by EarlGrey on 2007-03-15
Thanks for the reply, I run Edgy Eft and have two Sata disks. Sometimes the problem happens and sometimes all is fine for a day or two. Basically, I don't have a clue what does the error message mean. 

Data:
cat of /proc/mounts
```

rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw 0 0
/dev/sda1 / ext3 rw,data=ordered 0 0
/dev/sda1 /dev/.static/dev ext3 rw,data=ordered 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /lib/modules/2.6.17-11-generic/volatile tmpfs rw 0 0
tmpfs /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw 0 0
usbfs /dev/bus/usb/.usbfs usbfs rw 0 0
udev /proc/bus/usb tmpfs rw 0 0
usbfs /proc/bus/usb/.usbfs usbfs rw 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
/dev/sdb1 /media/carnivor ext3 rw,data=ordered 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0

```

uname -a
```

Linux vavrousek 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux

```

Shoud I post the hardware details as well?

---

