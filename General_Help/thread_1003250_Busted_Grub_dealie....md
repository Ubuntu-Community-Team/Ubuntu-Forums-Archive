---
title: "Busted Grub dealie..."
date: 2008-12-05
forum: General Help
---

### Post by Happypants on 2008-12-05
Alright... I've installed Fedora 10 along side Ubuntu.  I'm going to use GRUB as my booter, but it's causing me some issues.  

I didn't have Fedora install its loader so now I'm trying to get Ubuntu's to recognize it.  I've changed my menu.lst to have this entry at the very end (I'm not sure if placement matters, but that's where it is.

```
title           Fedora 10, kernel 2.6.27.5-117.fc10.x86_64
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.27.5-117.fc10.x86_64  root=UUID=c7f013fd-1c88-4298-8f9c-f349f8eb5d87
initrd          /boot/initrd.img-2.6.27.5-117.fc10.x86_64

```

My fdisk -l reads as this: (sda4 is where Fedora lives)

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xedaaedaa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6159    49472136   83  Linux
/dev/sda2           29693       30401     5695042+   5  Extended
/dev/sda3           10112       29692   157284382+  83  Linux
/dev/sda4            6160       10111    31744440   83  Linux
/dev/sda5           29693       30401     5695011   82  Linux swap / Solaris

Partition table entries are not in disk order

```

And edited my fstab to read as such (again, it's at the end and I don't know if that matters):

```
 # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=78560ee9-8789-481c-921e-ea4206b10584 /               ext3    relatime,erro$
# /dev/sda5
UUID=b4668d5d-f4ad-4704-87d8-7668dd18eed9 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/sda3 /home ext3 nodev,nosuid 0 2

# /dev/sda4
c7f013fd-1c88-4298-8f9c-f349f8eb5d87                    ext3    defaults 0 0


```

ls -lhat /dev/disk/by-uuid/ spits out:
```
drwxr-xr-x 2 root root 120 2008-12-05 21:12 .
drwxr-xr-x 6 root root 120 2008-12-05 21:12 ..
lrwxrwxrwx 1 root root  10 2008-12-05 21:12 c7f013fd-1c88-4298-8f9c-f349f8eb5d87 -> ../../sda4
lrwxrwxrwx 1 root root  10 2008-12-05 21:10 b4668d5d-f4ad-4704-87d8-7668dd18eed9 -> ../../sda5
lrwxrwxrwx 1 root root  10 2008-12-05 21:10 9e45ed3e-baed-4aff-8480-13716b530d87 -> ../../sda3
lrwxrwxrwx 1 root root  10 2008-12-05 21:10 78560ee9-8789-481c-921e-ea4206b10584 -> ../../sda1

```

I'm sure I'm missing something really obvious, but I've been screwing around with it for about the past two hours and my Googlefu failed me so I figured it's time to suck it up and ask for help.

Any advice you guys have to offer would be great.

Edit: Forgot to add that I have to load GRUB manually (hit esc) and it gives me an Error 15: file not found when I hit Fedora.  That might be good to know :)

---

### Post by Shazaam on 2008-12-05
Just a guess-
Put this...
```
UUID=
```
in front of this..
```
c7f013fd-1c88-4298-8f9c-f349f8eb5d87
```
in fstab?
Like so...
```
UUID=c7f013fd-1c88-4298-8f9c-f349f8eb5d87
```

You might want to fix this too (from your fdisk)...
```
Partition table entries are not in disk order
```

---

### Post by Happypants on 2008-12-05
> **Shazaam said:**
> Just a guess-
Put this...
```
UUID=
```
in front of this..
```
c7f013fd-1c88-4298-8f9c-f349f8eb5d87
```
in fstab?
Like so...
```
UUID=c7f013fd-1c88-4298-8f9c-f349f8eb5d87
```

/facepalm

Well... I knew I missed something simple.  Unfortunately that didn't fix the problem.  I'm still getting the same GRUB errors.  Thanks anyways.

---

### Post by Shazaam on 2008-12-05
Have you been here yet?...
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
Dual-boot page.

---

### Post by Happypants on 2008-12-06
> **Shazaam said:**
> Have you been here yet?...
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
Dual-boot page.

That post had a ton of useful info.  Thanks.

Unfortunately it didn't quite solve my problem I reinstalled Fedora and made sure that its boot loader was installed and edited my menu.lst to have them chain load.  Now it'll load Fedora but I still have to do it manually.  I'll get around to solving that problem later on (need to get my /home working for both of them not :) ).

---

