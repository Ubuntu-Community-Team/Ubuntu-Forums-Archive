---
title: "no longer will boot"
date: 2011-11-10
forum: Desktop Environments
---

### Post by houndhen on 2011-11-10
I multiboot my 32 bit desktop. I have windows xp on sda1. I use grub legacy for my boot menu.

My menu.lst entry for Ubuntu 10.10 gnome is:
```
title Ubuntu, with Linux 2.6.35-30-generic-pae
root (hd0,5)
kernel /boot/vmlinuz-2.6.35-30-generic-pae root=UUID=9e64fe77-49ad-4096-87a6-860982e9f15c ro quiet splash
initrd /boot/initrd.img-2.6.35-30-generic-pae
```The konsole output for the commnad 'blkid' is:
```
/dev/sda1: UUID="1CD0BAD8D0BAB77C" TYPE="ntfs" LABEL="windows_xp" 
/dev/sda5: UUID="d00fbeb3-c183-4d0a-b3f5-7293f8008bf2" TYPE="swap" 
/dev/sda6: LABEL="ubuntu" UUID="9e64fe77-49ad-4096-87a6-860982e9f15c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: LABEL="homeext3" UUID="2f8d3813-8770-4808-ba3a-53bcf99b7fc1" TYPE="ext3" 
/dev/sda8: UUID="ef543e2d-1dbd-4892-a5fa-1ba71a66fb6c" TYPE="ext3" LABEL="mepis" 
/dev/sda9: UUID="b10c2525-6d8d-4280-8cdb-4c45b47e8d4d" SEC_TYPE="ext2" TYPE="ext3" LABEL="sabayon" 
/dev/sda10: UUID="47d4b8de-262e-4f9d-8537-546e81c79f10" SEC_TYPE="ext2" TYPE="ext3" LABEL="chrunchbang" 
```The fstab file on /dev/sda6 is:
```
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=9e64fe77-49ad-4096-87a6-860982e9f15c /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=2f8d3813-8770-4808-ba3a-53bcf99b7fc1 /home           ext3    defaults,user_xattr        0       2
# swap was on /dev/sda5 during installation
UUID=871652bb-9e0d-46e4-8d26-a7fb61ef213d none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```/dev/sda7 is a 60 kb partition and contains a /home folder for each distro. I can boot into /dev/sda8, sda9, and sda10 but not sda6. It seems that the boot process can't mount the /home folder for sda6.

I haven't been able to find anything by searching the web and this forum that helps. Maybe I am not using the right words. Does someone have an idea of how to help with this dilemma?

Thanks,
Harold

after edit
for some reason after turning the computer off for the night; the next morning it booted like normal.

---

