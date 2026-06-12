---
title: "ext4 mount problem"
date: 2010-12-19
forum: Desktop Environments
---

### Post by Gusep on 2010-12-19
Hey all,

after a non standard reboot I'm experiencing problem with my hard drive. When I try to boot to my Ubuntu 10.04 installation a get the message "File not found" and grub rescue prompt. So I boot from my live USB and try to mount my hard drive. I get the error 

```

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda1 ..
```

when i check dmesg i can see the error

```
EXT4-fs (sda1): couldn't mount RDWR because of unsupported optional features (400000)

```
when i try fsck /dev/sda1 the output is

```
ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sda1 has unsupported feature(s): lazy_bg FEATURE_R22
e2fsck: Get a newer version of e2fsck!
```

could anyone provide any suggestions as what to do to save my ubuntu installation? thanks for your time guys..

---

### Post by dabl on 2010-12-19
From the Live CD, with the hard drive NOT mounted:

```
sudo e2fsck -pv /dev/sda1
```

Let it run to completion.

Then shutdown the Live CD session and try a reboot.

---

### Post by Gusep on 2010-12-21
hey dabl, thank you for the replay..

when I run the suggested command i get 

```
ubuntu@ubuntu:~$ sudo e2fsck -pv /dev/sda1
/dev/sda1 has unsupported feature(s): lazy_bg FEATURE_R22
e2fsck: Get a newer version of e2fsck!
```

any other suggestions?

---

### Post by dabl on 2010-12-21
It would appear that you have a damaged filesystem, due to the hard reboot probably.

If you look down toward the end of this thread, there are some pointers and a couple of links on how to find available alternate superblocks, and how to reassign one of them to your filesystem:

[http://www.linuxquestions.org/questions/linux-general-1/problems-mounting-ext3-drive-unknown-drive-parameters-713491/](http://www.linuxquestions.org/questions/linux-general-1/problems-mounting-ext3-drive-unknown-drive-parameters-713491/)

Obviously you will use e2fsck, not "fsck".  I'd backup all important data prior to running those commands.

---

### Post by psusi on 2010-12-21
Weird.  I don't know how on earth those flags could get set.  Try the backup copy of the superblock:

sudo e2fsck -f -b 32768 /dev/sda1

---

