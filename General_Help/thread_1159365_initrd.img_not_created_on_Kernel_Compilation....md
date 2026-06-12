---
title: "initrd.img not created on Kernel Compilation..."
date: 2009-05-14
forum: General Help
---

### Post by WitchCraft on 2009-05-14
Question, I compiled Linux kernel 2.6.29.3 as I compiled my last 5 kernels:

```

cd /usr/src
wget http://www.kernel.org/pub/linux/kern...6.29.3.tar.bz2
wget http://www.kernel.org/pub/linux/kern...3.tar.bz2.sign


apt-get update
apt-get install build-essential kernel-package libncurses5-dev fakeroot wget bzip2
apt-get upgrade
tar xjf linux-2.6.29.3.tar.bz2
ln -s linux-2.6.29.3 linux
cd /usr/src/linux


cp /boot/config-`uname -r` ./.config
make menuconfig

*** Build the kernel
make-kpkg clean
fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers


cd /usr/src
dpkg -i linux-image-2.6.29.3-custom_2.6.29.3-custom-10.00.Custom_i386.deb
dpkg -i linux-headers-2.6.29.3-custom_2.6.29.3-custom-10.00.Custom_i386.deb

shutdown -r now

```I realized that dpkg -i linux-headers-2.6.29.3-custom_2.6.29.3-custom-10.00.Custom_i386.deb was far faster than it had been before. I was suspicious, but then I just decided to restart and see.
When I restarted, I got this error message:
> 
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
Looking at /boot/grub/menu.lst
i saw that it lacked the 
initrd        /boot/initrd.img-2.6.29.3-custom
line

I added it, then restarted and got grub error 15 (file not found).

I looked into /boot/ and saw
>  
initrd.img-2.6.24-1-686
initrd.img-2.6.26-1-686
initrd.img-2.6.26-2-686
initrd.img-2.6.26-custom
initrd.img-2.6.28.1-custom
initrd.img-2.6.29-rc2-custom
which means i miss initrd.img-2.6.29.3-custom...

How can I correct that problem, and why is this at all ?
I've done nothing differently than in every kernel I compiled before...

---

### Post by WitchCraft on 2009-05-16
bump.

---

### Post by cmost on 2009-05-16
I'm not sure why you're not simply using the ready made Kernels avaiable here:  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.3/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.3/)

These install and run like a dream on Ubuntu 9.04 saving me lots of time and effort compiling my own.  Keep your eye out for the 2.6.30 which is at RC5 as we speak.

---

### Post by WitchCraft on 2009-05-16
> **cmost said:**
> I'm not sure why you're not simply using the ready made Kernels avaiable here:  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.3/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.29.3/")

These install and run like a dream on Ubuntu 9.04 saving me lots of time and effort compiling my own.  Keep your eye out for the 2.6.30 which is at RC5 as we speak.

I've the same problem with 2.6.39 RC5, I already tried this escape...

The problem is I have some (unusual) extra requirements, so I can't use the ready made Kernels.

I've compiled the kernel already several times with exactly this method, and it always worked until 2.6.29.3 came around...

Can this have something to do with the fact that I am no longer running gdm/kdm ?

---

### Post by cmost on 2009-05-16
Hmm, I can't see how GDM or KDM would have anything to do with the kernel.  Just for shits and giggles, have you tried this?

sudo gedit /etc/kernel-img.conf

edit to look like this: Note: lines prefaced by "#" are the original; the following line is the change.  Note:  yours might not look exactly like mine!

#postinst_hook = /sbin/update-grub
postinst_hook = update-grub
#postrm_hook = /sbin/update-grub
postrm_hook = update-grub
do_bootloader = no
do_symlinks = Yes
relative_links = Yes
#ramdisk = /usr/sbin/mkinitramfs
ramdisk = /usr/sbin/update-initramfs

Save the file

open a Terminal and then type:

sudo dpkg --configure -a

Viola! All errors (should now be) corrected and your new kernel and modules should be installed without issue!

---

### Post by WitchCraft on 2009-05-17
> **cmost said:**
> Hmm, I can't see how GDM or KDM would have anything to do with the kernel.  Just for shits and giggles, have you tried this?

sudo gedit /etc/kernel-img.conf

edit to look like this: Note: lines prefaced by "#" are the original; the following line is the change.  Note:  yours might not look exactly like mine!

#postinst_hook = /sbin/update-grub
postinst_hook = update-grub
#postrm_hook = /sbin/update-grub
postrm_hook = update-grub
do_bootloader = no
do_symlinks = Yes
relative_links = Yes
#ramdisk = /usr/sbin/mkinitramfs
ramdisk = /usr/sbin/update-initramfs

Save the file

open a Terminal and then type:

sudo dpkg --configure -a

Viola! All errors (should now be) corrected and your new kernel and modules should be installed without issue!

I have added  ramdisk = /usr/sbin/update-initramfs 
and run dpkg --configure -a

I've even recompiled the kernel, but,
However, that doesn't change anything.
What's the problem, damnit?

---

### Post by WitchCraft on 2009-05-17
OK, solved it:

In case anybody else has the problem

Generate the initramfs for your kernel manually:
```

update-initramfs -c -k 2.6.30-rc5-custom
update-initramfs -c -k 2.6.29.3-custom

```then add the initrd lines to /boot/grub/menu.lst
Looks like this (manually added part in bold)
```

title        Debian GNU/Linux, kernel 2.6.30-rc5-custom
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.30-rc5-custom root=/dev/hda3 ro quiet
**initrd        /boot/initrd.img-2.6.30-rc5-custom**

title        Debian GNU/Linux, kernel 2.6.30-rc5-custom (single-user mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.30-rc5-custom root=/dev/hda3 ro single
**initrd        /boot/initrd.img-2.6.30-rc5-custom**

title        Debian GNU/Linux, kernel 2.6.29.3-custom
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.29.3-custom root=/dev/hda3 ro quiet
**initrd        /boot/initrd.img-2.6.29.3-custom**

title        Debian GNU/Linux, kernel 2.6.29.3-custom (single-user mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.29.3-custom root=/dev/hda3 ro single
**initrd        /boot/initrd.img-2.6.29.3-custom**

title        Debian GNU/Linux, kernel 2.6.29-rc2-custom
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.29-rc2-custom root=/dev/hda3 ro quiet
initrd        /boot/initrd.img-2.6.29-rc2-custom

title        Debian GNU/Linux, kernel 2.6.29-rc2-custom (single-user mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.29-rc2-custom root=/dev/hda3 ro single
initrd        /boot/initrd.img-2.6.29-rc2-custom

```PS: I had a problem with "Waiting for /dev to be fully populated", where the boot process only resumed after "waiting for /dev" timed out.
Remove the quiet to see what the problem is (was the network card)

---

### Post by cmost on 2009-05-17
I'm glad you have it figured out!!  :D  So, now that the nonsense is over, how are you liking the 2.6.30 kernel?  I've shied away from that one myself due to its low RC number.  I do like the 2.6.29.3 kernel very much.  Any noticeable improvements in 2.6.30?

---

### Post by WitchCraft on 2009-05-18
> **cmost said:**
> I'm glad you have it figured out!!  :D  So, now that the nonsense is over, how are you liking the 2.6.30 kernel?  I've shied away from that one myself due to its low RC number.  I do like the 2.6.29.3 kernel very much.  Any noticeable improvements in 2.6.30?

I didn't try 2.6.29.3, I had 2.6.29-rc1, then straight went to 2.6.30-rc5.

So far, 2.6.30 seems to be quite a bit faster than 2.6.29. I didn't have to recompile ALSA, it worked for the first time without.

I like it - so far it's stable and it works.

---

### Post by WitchCraft on 2009-05-30
Update:

It looks like 2.6.30 rc 5 is unstable, it crashed several times.
(don't know whether it is the kernel or because of the update to glibc)

So I'm now going to recompile 2.6.30-rc7 and hope that then all problems are gone.

---

