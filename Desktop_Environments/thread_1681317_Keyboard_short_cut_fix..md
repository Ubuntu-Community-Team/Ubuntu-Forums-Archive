---
title: "Keyboard short cut fix."
date: 2011-02-04
forum: Desktop Environments
---

### Post by Lucas Azazer on 2011-02-04
Hello. I'm not sure if this is in the right section of the forums, so sorry if it's not.

I've been having problems with my desktop, nothing too bad, but anyways, I once knew someone who used to install Ubuntu onto people's desktops and he told me that he used some kind of keyboard shortcut to *fix any of his problems*. What this did was (I was told) was fix all the settings and such to be *as if* it were a *fresh install*.

My Question is, does *anyone know* this shortcut or does it even exist? 

At this point I care to know if the thing exist *more then* fixing my problem, it's driving me *crazy*,I've been hunting online and even downloaded some manuals. ... So any ideas?

Thanks.

[Edit] No key board shortcut afterall but the problem is ....

Well thanks for the answer about the keyboard short cut... so I guess my problem is that every time I download ANYTHING on ubuntu now, a window pops up saying

[SIZE="2"]"Package operation failed

The installation or removal of a software package failed.
Details:


installArchives() failed: Selecting previously deselected package totem-xine.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 252371 files and directories currently installed.)
Unpacking totem-xine (from .../totem-xine_2.32.0-0ubuntu1_all.deb) ...
Setting up linux-image-2.6.35-25-generic (2.6.35-25.44) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-25-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
 * dkms: running auto installation service for kernel 2.6.35-25-generic

 *       nvidia-current (260.19.06)...
   ...done.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
/etc/default/grub: 10: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-25-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-25-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-25-generic; however:
  Package linux-image-2.6.35-25-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.25.32); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up totem-xine (2.32.0-0ubuntu1) ...
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 linux-image-2.6.35-25-generic
 linux-image-generic
 linux-generic
Setting up linux-image-2.6.35-25-generic (2.6.35-25.44) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-25-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
 * dkms: running auto installation service for kernel 2.6.35-25-generic

 *       nvidia-current (260.19.06)...
   ...done.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
/etc/default/grub: 10: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-25-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-25-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-25-generic; however:
  Package linux-image-2.6.35-25-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.25.32); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
"[/SIZE]

I checked all my software sources and everything but I still have the problem. It's not that bad, the programs and updates installs but I constantly have to restart my computer when I do so. any ideas?

---

### Post by mcduck on 2011-02-04
Sorry, but no. There is no magical keyboard shortcut that would fix every problem, or even simply reset the installed system. :D

The easiest way to get everything back to as if the system was freshly installed is to make a fresh install... It's hard to say what type of shortcut or command your friend might have been actually talking about.

Anyway, if you post the problem you are having people here can probably help you with that.. :)

---

### Post by Copper Bezel on 2011-02-04
I suppose the friend could have been running inside Virtualbox the entire time. Then he could magically revert the system with a couple of clicks, at least. = )

---

### Post by Lucas Azazer on 2011-02-04
I reposted the problem up top.

---

