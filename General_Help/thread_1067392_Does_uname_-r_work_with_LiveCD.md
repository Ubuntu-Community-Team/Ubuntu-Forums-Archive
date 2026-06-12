---
title: "Does uname -r work with LiveCD?"
date: 2009-02-11
forum: General Help
---

### Post by Jammanuser on 2009-02-11
Hi all,
I was wondering if the command "uname -r" works booting from the LiveCD? Does the LiveCD have a kernel of its own, and if so, will that command print off the kernel of the LiveCD or of an Linux installation? and how 'bout if there's multiple installations of Linux on the same computer? what then?

Looking forward to the reply.

-Jam man

:guitar:

---

### Post by bodhi.zazen on 2009-02-11
yes it works ;)

uname -r will identify the current running kernel.

What is you are wanting ?

[http://linux.die.net/man/1/uname](http://linux.die.net/man/1/uname)

---

### Post by Jammanuser on 2009-02-11
> **bodhi.zazen said:**
> yes it works ;)

uname -r will identify the current running kernel.



Thanks. :) That's all I needed. I happen to be helping someone on another forum right now, who needed to know what his kernel was, and i told him to run that command to find out from the LiveCD, and he asked if it would return the kernel of his Fedora installation, or the one on his LiveCD, and I didn't know, so I came here. :guitar:

So I assume this means then that the one that will show up will be the one on the LiveCD?

Thanks for the reply.

-Jam man

:guitar:

---

### Post by Ahadiel on 2009-02-11
If you want to find out the kernel version of a linux installation FROM a livecd, you can usually just mount the '/' partition for the installation, then chroot into it.
ie.```
mkdir /mnt/foo
mount /dev/sda1 /mnt/foo
chroot /mnt/foo
uname -r
exit or CTRL+D to leave the chroot

```

---

### Post by bodhi.zazen on 2009-02-11
> **Ahadiel said:**
> If you want to find out the kernel version of a linux installation FROM a livecd, you can usually just mount the '/' partition for the installation, then chroot into it.
ie.```
mkdir /mnt/foo
mount /dev/sda1 /mnt/foo
chroot /mnt/foo
uname -r
exit or CTRL+D to leave the chroot

```

i have not tried that, but I do not think chroot will work (will try to test that).

You can of course ls /boot or grep vmlinuz /boot/grub/menu.lst

---

### Post by Ahadiel on 2009-02-11
> **bodhi.zazen said:**
> i have not tried that, but I do not think chroot will work (will try to test that).

You can of course ls /boot or grep vmlinuz /boot/grub/menu.lst
Ah yes, I just remembered. uname shows whichever kernel is running (wouldn't show the chroot'ed environment's kernel).

---

### Post by Jammanuser on 2009-02-11
> **bodhi.zazen said:**
> i have not tried that, but I do not think chroot will work (will try to test that).

You can of course ls /boot or grep vmlinuz /boot/grub/menu.lst

Ok...so what exactly does the "grep vmlinuz /boot/grub/menu.lst" command do? does it find the kernel on the Linux partition, because that's what I really need...:)

Thanks.

-Jam man

:guitar:

---

### Post by bodhi.zazen on 2009-02-12
> **Jammanuser said:**
> Ok...so what exactly does the "grep vmlinuz /boot/grub/menu.lst" command do? does it find the kernel on the Linux partition, because that's what I really need...:)

Thanks.

-Jam man

:guitar:

gerp is a search utility, it will search your grub configuration file (/boot/grub/menu.lst) for all kernels listed in grub.

The kernels are all in /boot, so you can also ```
ls /boot | grep vmlinuz
```

*both commands assume you are listing the /boot on your Fedora partition, so if you mount the Fedora partition on a live CD at say /media/fedora, use

[ls /media/fedora/boot | grep vmlinuz[/code]

---

### Post by Jammanuser on 2009-02-12
> **bodhi.zazen said:**
> gerp is a search utility, it will search your grub configuration file (/boot/grub/menu.lst) for all kernels listed in grub.

The kernels are all in /boot, so you can also ```
ls /boot | grep vmlinuz
```

*both commands assume you are listing the /boot on your Fedora partition, so if you mount the Fedora partition on a live CD at say /media/fedora, use

[ls /media/fedora/boot | grep vmlinuz[/code]

Ok...so what you're basically saying is you have to first mount the Fedora partition via the Terminal before it will work? I guess that explains then why I got the "no such file or command" message when testing that command from a LiveCD just a little while ago....:lolflag: So what's the best (and easiest) method then of mounting the Fedora partition via the terminal before running the above commands?

Would I just do:
```

sudo mkdir /media
sudo mount /dev/sdxy /media

```
and then run the commands you mentioned...where the "x" and the "y" are replaced with the appropriate disk and partition numbers of the Fedora partition?

-Jam man

:guitar:

---

### Post by bodhi.zazen on 2009-02-12
yes

sudo mkdir /media/fedora

sudo fdisk -l

sudo mount /dev/sdxy /media/fedora

ls /media/fedora/boot | grep vmlinuz

The only "trick" may be that by default Fedora uses LVM , so you may (or may not) have a separate /boot partition (separate from the fedora root).

---

### Post by Jammanuser on 2009-02-12
> **bodhi.zazen said:**
> yes

sudo mkdir /media/fedora

sudo fdisk -l

sudo mount /dev/sdxy /media/fedora

ls /media/fedora/boot | grep vmlinuz

The only "trick" may be that by default Fedora uses LVM , so you may (or may not) have a separate /boot partition (separate from the fedora root).

Thanks, but wouldn't it make more sense to do something like:

```
sudo fdisk -l
sudo mkdir /fedora
sudo mount /dev/sdxy /fedora
ls /fedora/boot | grep vmlinuz
```

?

why have the extra "media" folder to get through?

Anyway, thanks for the info, and I believe this will work. :)

-Jam man

:guitar:

---

