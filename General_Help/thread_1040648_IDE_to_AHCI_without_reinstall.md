---
title: "IDE to AHCI without reinstall?"
date: 2009-01-15
forum: General Help
---

### Post by bilboe on 2009-01-15
Hello There!
I recently built a computer with a SATA hard drive and CD drive. 
My motherboard default setting is to have SATA drives emulate and appear as IDE, which i did not know when I installed Ubuntu.

My question is this: is there a way to switch the BIOS to AHCI mode without having to reinstall Ubuntu? If not, is there a way to reinstall ubuntu so all of my settings and files are still there?

Thank you!

---

### Post by rbmorse on 2009-01-15
AHCI drivers are built into the Linux kernel.  Just change the setting in your BIOS setup, save and  restart. When the machine reboots Linux will load the proper drivers. 

No other actions on your part are required.

---

### Post by Jens.L on 2011-01-31
Hi.

If i change from Native IDE(installed with that) to AHCI my grub won't boot. I just get to the grub cli.  
I forgot to change from Native IDE to AHCI when i installed Ubuntu 10.10. And it's to much work to reinstall just to change to AHCI.

What can i do?

---

### Post by meijer.o on 2011-01-31
Dear linux user:

use a terminal e.g. gnome-terminal and login as root:

modify this file:

/etc/initramfs-tools/modules

add the modules:
ahci
libahci

modify then this file:
/etc/initramfs-tools/initramfs.conf

and change < most > into < list>

run:
update-initramfs -u


reboot and change your bios settings to ahci, your computer should boot now.

If needed, undo the changes of the files, (in case of any  problems after boot) and:

re-run: update-initramfs -u 

It should work,

Otto Meijer

---

### Post by Jens.L on 2011-02-01
Thanks for the help but it didn't work. 

Still just getting this screen after i change to AHCI mode in bios.

[http://members.iinet.net.au/~herman546/p15/fig2grub.gif](http://members.iinet.net.au/~herman546/p15/fig2grub.gif)

---

### Post by meijer.o on 2011-02-01
Are you sure you rebuilt the initramfs?
Can you boot from a live-cd with AHCI

Please post after modification:

/etc/initramfs-tools/modules
/etc/initramfs-tools/initramfs.conf

1 run: update-initramfs -u
2 run: ls -l /boot > /boot.txt



post the resulting file /boot.txt after command 2

all as root

Succes:

Otto Meijer

---

### Post by Jens.L on 2011-02-01
Ya i did your step with sudo -s and if i check the files again they are correct.
Gonna try to boot with an live-cd in ahci and check if i can reinstall grub/burg
from the recovery console.

```
totalt 57260
-rw-r--r-- 1 root root   700477 2010-10-17 02:37 abi-2.6.35-22-generic
-rw-r--r-- 1 root root   700601 2010-12-02 07:33 abi-2.6.35-24-generic
-rw-r--r-- 1 root root   700601 2011-01-21 23:11 abi-2.6.35-25-generic
drwxr-xr-x 5 root root    12288 2011-02-01 17:35 burg
-rw-r--r-- 1 root root   122604 2010-10-17 02:37 config-2.6.35-22-generic
-rw-r--r-- 1 root root   122626 2010-12-02 07:33 config-2.6.35-24-generic
-rw-r--r-- 1 root root   122627 2011-01-21 23:11 config-2.6.35-25-generic
drwxr-xr-x 3 root root     4096 2011-01-29 17:42 grub
-rw-r--r-- 1 root root 11003307 2011-01-12 00:33 initrd.img-2.6.35-22-generic
-rw-r--r-- 1 root root 16711631 2011-01-20 02:05 initrd.img-2.6.35-24-generic
-rw-r--r-- 1 root root  8011446 2011-02-01 22:22 initrd.img-2.6.35-25-generic
-rw-r--r-- 1 root root   165084 2010-09-24 20:16 memtest86+.bin
-rw-r--r-- 1 root root   167264 2010-09-24 20:16 memtest86+_multiboot.bin
-rw-r--r-- 1 root root  2342386 2010-10-17 02:37 System.map-2.6.35-22-generic
-rw-r--r-- 1 root root  2343073 2010-12-02 07:33 System.map-2.6.35-24-generic
-rw-r--r-- 1 root root  2343087 2011-01-21 23:11 System.map-2.6.35-25-generic
-rw-r--r-- 1 root root     1335 2010-10-17 02:41 vmcoreinfo-2.6.35-22-generic
-rw-r--r-- 1 root root     1336 2010-12-02 07:36 vmcoreinfo-2.6.35-24-generic
-rw-r--r-- 1 root root     1336 2011-01-21 23:17 vmcoreinfo-2.6.35-25-generic
-rw-r--r-- 1 root root  4336016 2010-10-17 02:37 vmlinuz-2.6.35-22-generic
-rw-r--r-- 1 root root  4338064 2010-12-02 07:33 vmlinuz-2.6.35-24-generic
-rw-r--r-- 1 root root  4340432 2011-01-21 23:11 vmlinuz-2.6.35-25-generic
```Edit: Booted from the livecd and chroot my filesystem and reinstalled grub/burg but still the same.
Edit2: SOLVED: Chrooted from the livecd again and reinstalled burg and did update-burg and update-initramfs. But i figured it out that it was the vista chainloading that mess up burg.

---

### Post by meijer.o on 2011-02-01
The cause must be in the initramfs. As the ahci module should be loaded by it. Otherwise you cannot boot. Good you solved it.

best regards,
Otto

---

### Post by cphuntington97 on 2011-11-15
Hello. I am in the same situation as Jens.L, though the changes have not been successful for me. 

Ubuntu Server 10.04.3 LTS is the only OS on this system.

Linux fs4 2.6.32-35-generic #78-Ubuntu SMP Tue Oct 11 16:11:24 UTC 2011 x86_64 GNU/Linux


initramfs.conf
#
# initramfs.conf
# Configuration file for mkinitramfs(8). See initramfs.conf(5).
#

#
# MODULES: [ most | netboot | dep | list ]
#
# most - Add all framebuffer, acpi, filesystem, and harddrive drivers.
#
# dep - Try and guess which modules to load.
#
# netboot - Add the base modules, network modules, but skip block devices.
#
# list - Only include modules from the 'additional modules' list
#

MODULES=list

#
# BUSYBOX: [ y | n ]
#
# Use busybox if available.
#

BUSYBOX=y

#
# COMPCACHE_SIZE: [ "x K" | "x M" | "x G" | "x %" ]
#
# Amount of RAM to use for RAM-based compressed swap space.
#
# An empty value - compcache isn't used, or added to the initramfs at all.
# An integer and K (e.g. 65536 K) - use a number of kilobytes.
# An integer and M (e.g. 256 M) - use a number of megabytes.
# An integer and G (e.g. 1 G) - use a number of gigabytes.
# An integer and % (e.g. 50 %) - use a percentage of the amount of RAM.
#
# You can optionally install the compcache package to configure this setting
# via debconf and have userspace scripts to load and unload compcache.
#

COMPCACHE_SIZE=""

#
# NFS Section of the config.
#

#
# BOOT: [ local | nfs ]
#
# local - Boot off of local media (harddrive, USB stick).
#
# nfs - Boot using an NFS drive as the root of the drive.
#

BOOT=local

#
# DEVICE: ...
#
# Specify the network interface, like eth0
#

DEVICE=eth0

#
# NFSROOT: [ auto | HOST:MOUNT ]
#

NFSROOT=auto
-----------------
modules
# List of modules that you want to include in your initramfs.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
# sd_mod
ahci
libahci

------------------

ls -l /boot
total 9799
-rw-r--r-- 1 root root  646700 2011-10-11 12:56 abi-2.6.32-35-generic
-rw-r--r-- 1 root root  110578 2011-10-11 12:56 config-2.6.32-35-generic
drwxr-xr-x 3 root root    7168 2011-11-15 10:24 grub
-rw-r--r-- 1 root root 2880820 2011-11-15 10:24 initrd.img-2.6.32-35-generic
drwx------ 2 root root   12288 2011-11-11 09:55 lost+found
-rw-r--r-- 1 root root  160280 2010-03-23 05:40 memtest86+.bin
-rw-r--r-- 1 root root 2157735 2011-10-11 12:56 System.map-2.6.32-35-generic
-rw-r--r-- 1 root root    1336 2011-10-11 12:56 vmcoreinfo-2.6.32-35-generic
-rw-r--r-- 1 root root 4053216 2011-10-11 12:56 vmlinuz-2.6.32-35-generic




I ran sudo update-initramfs -u and sudo update-grub

System still only boots in IDE mode. Blinking cursor when set to AHCI. 

If I can't get the AHCI mode working, I lose two sata ports (they are Marvell SATA 88SE917X). My mainboard is Intel DH61BE with the newest bios.

In AHCI mode, I can boot to cd and select "boot to first hard drive" and it loads fine.

Thanks for help...

---

