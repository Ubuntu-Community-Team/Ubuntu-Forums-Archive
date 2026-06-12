---
title: "Major 9.4 upgrade issue"
date: 2009-01-22
forum: General Help
---

### Post by yoman82 on 2009-01-22
When upgrading to 9.4, my catalyst driver stopped working, which was to be expected. But also, when upgrading, my dpkg started popping out random cryptic error messages about kernels not being configured and the like. My system stopped booting normally, claiming an X11 mount error, saying it could not find monitor :0. Then, I booted into recovery mode, and selected the fix broken packages option. Bad idea. It went into an endless loop, returning the same errors over and over. I was forced to hard reboot. Now, when I select the newest kernel, it replies "error 24: attempt to access block outside partition" and returns me to Grub. Help!!!!

---

### Post by pennacook on 2009-01-22
What does your boot line state? Make sure it is pointing to the correct hd.

---

### Post by yoman82 on 2009-01-22
I only have on hard drive installed, and only one partition on that.

---

### Post by yoman82 on 2009-01-22
Setting up linux-image-2.6.28-4-generic (2.6.28-4.11) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-4-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... found: (hd0,0)/boot/grub/splashimages/earth-horizon.xpm.gz

expr: non-numeric argument
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.28-4-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.28-4-generic; however:
  Package linux-image-2.6.28-4-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-2.6.27-11-generic (2.6.27-11.23) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.27-11-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.27-11.22 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.27-11.22 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... found: (hd0,0)/boot/grub/splashimages/earth-horizon.xpm.gz

expr: non-numeric argument
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.27-11-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.28.4.4); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.28-4-generic:
 linux-restricted-modules-2.6.28-4-generic depends on linux-image-2.6.28-4-generic; however:
  Package linux-image-2.6.28-4-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.28-4-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.28-4-generic; however:
  Package linux-restricted-modules-2.6.28-4-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules:
 linux-restricted-modules depends on linux-restricted-modules-generic (= 2.6.28.4.4); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-restricted-modules (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.28-4-generic
 linux-image-generic
 linux-image-2.6.27-11-generic
 linux-generic
 linux-restricted-modules-2.6.28-4-generic
 linux-restricted-modules-generic
 linux-restricted-modules

---

### Post by dcstar on 2009-01-22
> **yoman82 said:**
> When upgrading to 9.4, my catalyst driver stopped working, which was to be expected. But also, when upgrading, my dpkg started popping out random cryptic error messages about kernels not being configured and the like. My system stopped booting normally, claiming an X11 mount error, saying it could not find monitor :0. Then, I booted into recovery mode, and selected the fix broken packages option. Bad idea. It went into an endless loop, returning the same errors over and over. I was forced to hard reboot. Now, when I select the newest kernel, it replies "error 24: attempt to access block outside partition" and returns me to Grub. Help!!!!

9.04 is **ALPHA** software, all things are not meant to work yet because it is still being developed.

Report the problem to the developers, that is what they are doing right now - it is inappropriate to ask for support for unreleased versions.

---

### Post by yoman82 on 2009-01-23
I cannot. Apport refuses to report anything, it srashes each time I load it with no error message.

---

### Post by yoman82 on 2009-01-24
*Bump* I need some help fairly bad.

---

### Post by diablo75 on 2009-01-24
> **yoman82 said:**
> *Bump* I need some help fairly bad.

You should probably try using 8.10 or earlier.  9.04 is UNSTABLE and UNDER DEVELOPMENT!

---

### Post by PmDematagoda on 2009-01-24
At OP:- As stated before, Ubuntu 9.04 is still under development(heavy development I might add since it hasn't even hit beta as of yet), so if you cannot handle the troubles and instabilities you get by running alpha software, then you should not use it until it is released as stable.

Please use 8.10 until 9.04 is released, but if you still wish to test 9.04(you should test, not use it for production purposes) then you should consider posting your problems [here]("http://ubuntuforums.org/forumdisplay.php?f=352").

---

### Post by yoman82 on 2009-01-25
Is there any way to temporarily downgrade?

---

### Post by diablo75 on 2009-01-25
> **yoman82 said:**
> Is there any way to temporarily downgrade?

Backup the contents of your home folder, format your hard drive and install a stable, supported version.  Then copy whatever you need from your backup back into your home folder.  If it were me, I would back up my .mozilla folder, open up Evolution and export a backup tar.gz (to be imported later) and any other personal files I might want (documents, music, videos, etc).  You could spend days/weeks trying to figure out how to downgrade from broken alpha software, or a few hours doing it this way and save yourself from a lot of headaches.

---

### Post by yoman82 on 2009-01-25
I guess I am forced to stick with 9.04, as I have no time to re-install, and no sufficient medium to back up my configuration.

---

### Post by cariboo on 2009-01-25
I would suggest you head to [Jaunty Testing and Discussion]("http://ubuntuforums.org/forumdisplay.php?f=352") and check out the threads to solve some of your problems.

Before upgrading, you should check the [Release Notes]("http://www.ubuntu.com/testing/jaunty/alpha3").

Jim

---

