---
title: "Upgrading Xubuntu 8.04 to 10.04 - no starting up (GRUB?)"
date: 2010-12-29
forum: Desktop Environments
---

### Post by Skara Brae on 2010-12-29
So, I have Ubuntu 10.04 and Xubuntu (together with that other, proprietary OS) in triple-boot, all OS's nicely in the GRUB menu.

I have just finished upgrading Xubuntu 8.04 to Xubuntu 10.04, and the upgrade seems to have gone well.

But after rebooting, Xubuntu 10.04 will not start--that is, it is not in the GRUB menu--that is, the GRUB menu still shows the Xubuntu 8.04 lines (Xubuntu 8.04 with 3 different kernels).

When I choose the Xubuntu 8.04 line with the "latest" kernel ("something-28", don't know by heart), I end up with a black Terminal-like monitor screen and the following text:

**********************************************************
[I]mount: mounting none on /dev failed: No such device
udevd(878 ): error getting socket: Invalid argument

error initizalizing netlink socket
udevd(878 ): error initializing netlink socket

libudev: udev_monitor_new_from_netlink: error getting socket: Invalid argument
Segmentation fault
Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
-- Check rootdelay= (did the system wait long enough?)
-- Check root= (did the system wait for teh right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/acdc1930-3c59-4ea0-ae32-30e0b1ee7d9d does not exist. Dropping to a shell!

Busybox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _[/I]

**********************************************************

I am just a "n00b-with-some-Linux-knowledge", so the above might as well have been in Russian...

I assume the (main?) problem is in the GRUB menu, which still shows the Xubuntu 8.04 entries with 3 different kernels. I didn't think of a possible GRUB issue, when I started upgrading :)

Is there a way to fix this, so that I can boot Xubuntu 10.04, too?

(I made a few pictures with my Samsung G400 cellphone, but that does not mount in Ubuntu (I thought that it did), also not in XP-in-Virtualbox, so I can not get to the pictures right now.)

Thank you for any help...

-Skara

[edit] Oops, does this post belong in this thread?

---

### Post by Brandon Williams on 2010-12-31
My guess is that grub is configured to look at your Ubuntu partition for its configuration. Boot into Ubuntu and run 'sudo update-grub', which should automatically discover the new Xubuntu information and fix the config file used by grub at boot.

If that doesn't help, we'll need to get more information from you and take more complicated recovery action.

---

### Post by Skara Brae on 2011-01-01
*sudo update-grub*

Is it _that_ easy? :eek:

Brandon Williams,
Yes, it was _that_ easy! I am now writing this in Xubuntu 10.04. Awesome!

-oo-

On a sidenote, every time again I am awed by how "amazing" Linux (Ubuntu and Xubuntu, in this case) is. Here I was, thinking that "fixing" that Xubuntu upgrade would take quite some effort, but all it took was that short command. Incredible. (Incredible, compared to that awful MS Windows, which I have worked with since Win95, and which does not even have a bootloader--on purpose.)

The more I work with Linux (Ubuntu, Xubuntu), the more I "love" it. I just find it an amazing thing. I am sitting here, just going "*wow, that was it?*" ("sudo update-grub", I mean).

GNU/Linux is one of the greatest things that have been done, in my opinion.

Brandon Williams, thank you _so_ much. You have literally saved a Xubuntu installation (I was already thinking of just turning the Xubuntu partition into a plain "data" partition).

Oh, Xubuntu runs very fast on this PC :p (Specs in my signature)

---

### Post by Skara Brae on 2011-01-01
By the way, just as information, this is what I got after the "update-grub":

-----------------------------------------------------
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-27-generic
Found initrd image: /boot/initrd.img-2.6.32-27-generic
Found linux image: /boot/vmlinuz-2.6.32-26-generic
Found initrd image: /boot/initrd.img-2.6.32-26-generic
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows XP Home on /dev/sda1
Found Ubuntu 10.04.1 LTS (10.04) on /dev/sda2
-----------------------------------------------------

(That "25" kernel can be removed; and that I know how to do!)

I am a happy GNU/Linux user :lolflag:

---

### Post by Brandon Williams on 2011-01-02
> **Skara Brae said:**
> Yes, it was _that_ easy! I am now writing this in Xubuntu 10.04. Awesome!

Great. Glad you got it working.

With your current config, you'll have to boot into the primary install and run update-grub whenever your install a kernel update or perform a release upgrade in the non-primary installation. You might want to consider chainloading your non-primary installations. This would allow you to avoid running update-grub in the primary install when you upgrade a non-primary install.

The idea is to install grub separately to the root parition for each individual non-primary install (e.g. Xubuntu in this case). Then, in the primary install, add a custom entry to chainload from the non-primary installation. [Here](https://help.ubuntu.com/community/Grub2#Custom Menu Entries) is information about creating custom menu entries with an example of an entry to chainload another copy of grub. I think there's a way to configure grub in the primary install so that it doesn't probe the non-primary install partitions, but it's best to make sure that chainloading is working first.

---

### Post by Brandon Williams on 2011-01-02
oops. double-posted.

---

### Post by AgentLeMan on 2011-02-10
Hey Guys!

At the moment, I have the exact same problem with my Ubuntu 10.04 installation! I have just finished upgrading from 8.04 to 10.04 and I am experiencing the exact same problem as Skara!

I know that Brandon suggested booting into Ubuntu and using 'sudo update-grub' but my question is: how EXACTLY do I boot into Ubuntu? I tried booting from a LiveCD of Ubuntu 10.04, but when I typed "sudo update-grub' into a terminal window I got this error:

 /usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

Any help that either of you can provide will be most helpful!!!

---

