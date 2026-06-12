---
title: "Displaying boot message in Dapper"
date: 2006-06-08
forum: Desktop Environments
---

### Post by gspr on 2006-06-08
Hi.

How do I turn off that huge (K)ubuntu logo and meaningless abridged boot message, and have my Dapper system just display normal boot messages?
Thanks.

(Sorry if this is the wrong part of the forum.)

---

### Post by ns2048 on 2006-06-08
Hello,

Try removing the kernel parameters 'quiet splash' from your GRUB config file '/boot/grub/menu.lst'

EXAMPLE (graphical bootup with abridged messages)

title           Ubuntu, kernel 2.6.15-23-686
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-23-686 root=/dev/hda2 ro acpi=off quiet splash
initrd          /boot/initrd.img-2.6.15-23-686
boot

To disable graphical bootup, remove the two parameters 'quiet' and 'splash' from the line above starting with 'kernel' so that it looks like this.

kernel          /boot/vmlinuz-2.6.15-23-686 root=/dev/hda2 ro acpi=off

Hope that helps.

-- ns2048

---

### Post by gspr on 2006-06-08
Thanks a bunch!

Another question: Is /boot/grub/menu.lst intended for user editing?
I've been a Gentoo user for many years, and am very accustomed to doing everything myself. I am, however, trying to learn to not interfere with my distro, now that I've switched to Ubuntu. Is there some tool that should be used for editing menu.lst, or should I just go ahead and edit as I would with Gentoo?

Thanks again.

---

### Post by Nonno Bassotto on 2006-06-08
Up to now you still have to edit it by hand. I remember seeing some projects of a grub graphical configuration utility, but I'm not sure; anyway it is not standard in the distro.

---

### Post by gspr on 2006-06-10
OK. Thanks for the help.

---

