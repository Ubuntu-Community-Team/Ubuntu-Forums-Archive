---
title: "firewire 1394 HFS+ drive write problems"
date: 2006-03-02
forum: Desktop Environments
---

### Post by macsimski on 2006-03-02
Hello all, on my kubuntu breezy dell optiplex i have mounted my mac hfs plus drive via firewire. But i can not write or change something to it. i get the following error: ```
simon@atxbuntu:/media/sda3$ sudo rm BootX.image rm: cannot remove `BootX.image': Read-only file system
``` my mount looks like this: ```
simon@atxbuntu:/$ mount /dev/hda1 on / type ext3 (rw,errors=remount-ro) proc on /proc type proc (rw) sysfs on /sys type sysfs (rw) devpts on /dev/pts type devpts (rw,gid=5,mode=620) tmpfs on /dev/shm type tmpfs (rw) usbfs on /proc/bus/usb type usbfs (rw) tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755) tmpfs on /dev type tmpfs (rw,size=10M,mode=0755) /dev/sda3 on /media/sda3 type hfsplus (rw)
``` and i have also problems mounting the drive on the fly. it simply will not mount automatically when plugged in. but when i boot up with the drive connected, it will show up as ext1 on my desktop. i used the command ```
 mount -w -t hfsplus /dev/sda3 /media/sda3
``` to mount it manually, but any action in the terminal to alter the disk will state that it is mounted read only??? anyone?

<update>
I did a dmesg | tail and it gave me:

```
[4299075.118000] SCSI device sda: 490234752 512-byte hdwr sectors (251000 MB)
[4299075.118000] sda: asking for cache data failed
[4299075.118000] sda: assuming drive cache: write through
[4299075.134000] SCSI device sda: 490234752 512-byte hdwr sectors (251000 MB)
[4299075.134000] sda: asking for cache data failed
[4299075.134000] sda: assuming drive cache: write through
[4299075.134000]  /dev/scsi/host0/bus0/target0/lun0: [mac] p1 p2 p3 p4
[4299075.158000] Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
[4299081.165000] HFS+-fs warning: Filesystem was not cleanly unmounted, running fsck.hfsplus is recommended.  mounting read-only.

```

which explanes why it is mounted read only! It's a pity that there is no feedback for that in the gui. i will post results after running fsck.hfsplus (if i can find where it is located...)

---

### Post by macsimski on 2006-03-04
well,

after trying to find fsck.hfsplus on my system, and not finding it, despite I installed the hfsplus package in adept... i went to gogle and looked for the string fsck.hfsplus. it turns out that the tool actually is called hpfsck!!!??? Very logical of course. Anyway, it did'nt do the job. running hpfsck on dev/sda3 gave me a error that this was not a hfs+ disk.

So i unhooked the drive from my Kubuntu box and attached it to my mac to use disk utility to fix it. it found no errors. the i hooked it up to mu Kubuntu again and voila. it mounted read/write!

so mount gives you not allways the right info. it sead that it mounted /dev/sda3 read write, but that was not the case.

---

