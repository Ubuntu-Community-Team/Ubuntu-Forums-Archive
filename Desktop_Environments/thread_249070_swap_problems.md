---
title: "swap problems"
date: 2006-09-02
forum: Desktop Environments
---

### Post by col.panic on 2006-09-02
So i loaded ubuntu onto mylappy a week ago and it was kinda a wierd installation that i won't bore you with.  I opened up my system monitor.  and noticed that my swap partition is not being used... i dunno any suggestions?

---

### Post by SkyNet2029 on 2006-09-02
Check the output of 

```
$more /etc/fstab
```

to ensure that your swap is listed as mountable during bootup for starters.
You could also run

```
$sudo mount -a
```

to see if that outputs any errors as to swap mounting.
or, you could manually mount swap and then check to see usage while running something that is swap-intensive in usage, like Gimp or Blender once the swap is enabled.

```
$sudo swapon /dev/hdxx
```

replacing the /hdxx with the proper drive of your swap. If its already mounted and not actually being used, the error output should be like this:

```
swapon: /dev/hdb2: Device or resource busy
```.

It could be that your system doesn't really need to use the swap file for whatever tasks you were doing at the time you checked its usage.

---

### Post by col.panic on 2006-09-04
so this is what more output

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hda2       /home           ext3    defaults        0       0

```

nothing out of the ordinary here i don't think i'm 99% sure that hda5 is the extended swap partition

```
$ sudo mount -a
[mntent]: line 6 in /etc/fstab is bad
mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

as for mounting swap this is what happened i think it means its mounted already...  ```
$ sudo swapon /dev/hda5
swapon: /dev/hda5: Invalid argument

``` when I open up my system monitor it says that i am using 0% of 0 kB of swap so i know it hasn't loaded properly... As for if my system needs the swap .. well it does one of the reasons that this is such a problem for me is that when I run out of physical ram my system freezes and becomes unstable.  Any other sugestions??? Could it be grub???

---

### Post by anaconda on 2006-09-04
maybe your swap partition has,t been made to be swap ??

mkswap /dev/hda5
swapon /dev/hda5

should take your swap in use.

---

### Post by col.panic on 2006-09-04
Thanks a lot that totally fixed it.  Thanks both of you... very helpful and i learned a bit along the way

---

