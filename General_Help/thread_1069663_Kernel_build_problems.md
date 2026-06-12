---
title: "Kernel build problems"
date: 2009-02-14
forum: General Help
---

### Post by dooferlad on 2009-02-14
Hi,

I am using Ubuntu server and I have a Via C7 CPU. The CPU doesn't do frequency scaling with the stock kernel so I built a new one (2.6.28.3) using the same basic config as the stock kernel but with the C7 frequency scaling module included this time (for some reason it is the only one left out). I am having problems booting it though. I keep getting a kernel panic:

VFS: Unable to mount root fs on unknown - block(0,0)

I haven't built an initrd file system and have disabled the initial ram fs option in the kernel, so I shouldn't need it. I have got EXT3 built into the kernel. My grub config for the kernel is (I have tried both options):

title           My 2.6.28.3 kernel
uuid            142d6c44-c4b8-4398-b04a-df4ea62da804
kernel          /vmlinuz-2.6.28.3 root=UUID=2e88fc9f-f09a-4f6a-a7d6-999da2b2f1a3 ro quiet

title           My 2.6.28.3 kernel
kernel          (hd0,2)/vmlinuz-2.6.28.3 root=/dev/sda1 ro quiet

And my fstab is:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2e88fc9f-f09a-4f6a-a7d6-999da2b2f1a3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/mapper/backup-backup--volume
UUID=23188f97-24d9-496d-af6c-7253662bd17c /backup         ext3    relatime        0       2
# /dev/sda3
UUID=142d6c44-c4b8-4398-b04a-df4ea62da804 /boot           ext3    relatime        0       2
# /dev/sda5
UUID=cab81c8d-e2dd-46e9-ac2d-0502a29bc3c4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

As far as I can tell my parameters are right. My next thought is that perhaps the kernel needs a module to access my disk that isn't built in. It isn't exactly a quick machine though so rebuilding and installing kernels is quite a chore. Anyone got any ideas?

---

### Post by dooferlad on 2009-02-15
I have seen the light and followed [https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild) - no more make, make install for me.

Old habits die hard I guess...

It does work though :-)

---

