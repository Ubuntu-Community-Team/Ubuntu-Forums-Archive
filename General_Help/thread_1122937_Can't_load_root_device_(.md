---
title: "Can't load root device :("
date: 2009-04-11
forum: General Help
---

### Post by Cesaar on 2009-04-11
I'm having problems to run Ubuntu with the usual usual Ubuntu 8.10, kernel 2.6.27-11-generic. This happened after some update. When I just turn on my laptop and let it go, it gets to the loading screen and it freezes. Then, immediately after, the screen begins to distort until it is just black... 
So, I loaded the Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode), instead, by pressing 'esc' at boot. And it shows me this error:
```

Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/96a5951d-94e2-4aea-9e25-0097e21a27da does not exist. Dropping to a shell!


BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initframfs) _
```

I used the older kernel: Ubuntu 8.10, kernel 2.6.27-7-generic, and Ubuntu loads just fine.
***I looked in the '/dev/disk' folder and there is no "by-uuid" folder which could be the cause of the problem.*** I'm not sure how to fix this problem. The Only way I can get Ubuntu to run is to use the older kernel.

Can somebody help please?

---

### Post by Wayne_V on 2009-04-11
Try removing the newer kernel and reinstalling:

$ sudo apt-get purge linux-image-2.6.27-11-generic
(make sure you review the packages that are going to be removed so there are no surprises ...)

$ sudo apt-get update ; sudo apt-get dist-upgrade
-- or --
$ sudo apt-get install linux-image-2.6.27-11-generic

---

### Post by Cesaar on 2009-04-12
> Try removing the newer kernel and reinstalling
Thanks Wayne_V. I have done what you said but it didn't work. The kernel still doesn't work correctly and having the same problems. I thought the installation file might have gotten corrupted so in the synaptic package manager I re-downloaded it but apparently that's not the issue.

I'm not sure what's causing the problem. Any ideas?

---

### Post by Wayne_V on 2009-04-13
did you use the 'apt-get purge' to completely remove the old kernel?

---

### Post by Cesaar on 2009-04-22
> **Wayne_V said:**
> did you use the 'apt-get purge' to completely remove the old kernel?

Do you mean the newer kernel? If so, I did remove and reinstalled the newer kernel just as you mentioned. Otherwise, I didn't try that for the older  kernel. However, if I purge the older kernel and the newer one is not working, isn't possible that I won't be able to run Ubuntu at all? Or are you suggesting a conflict between kernels so that in order to have the newer kernel runnig I must remove the older one? Thanks for your attention by the way and sorry for my slow reply.

---

### Post by Wayne_V on 2009-04-22
Yes - that is a little ambiguous.  I meant to 'apt-get purge <kernel that fails to boot>'.

Make sure you use purge and not remove -- this will completely remove the package.

Can you post your /boot/grub/menu.lst ?

---

### Post by Cesaar on 2009-04-23
> **Wayne_V said:**
> Yes - that is a little ambiguous.  I meant to 'apt-get purge <kernel that fails to boot>'.

Make sure you use purge and not remove -- this will completely remove the package.

Can you post your /boot/grub/menu.lst ?
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=96a5951d-94e2-4aea-9e25-0097e21a27da ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=96a5951d-94e2-4aea-9e25-0097e21a27da

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		96a5951d-94e2-4aea-9e25-0097e21a27da
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=96a5951d-94e2-4aea-9e25-0097e21a27da ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		96a5951d-94e2-4aea-9e25-0097e21a27da
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=96a5951d-94e2-4aea-9e25-0097e21a27da ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		96a5951d-94e2-4aea-9e25-0097e21a27da
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=96a5951d-94e2-4aea-9e25-0097e21a27da ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		96a5951d-94e2-4aea-9e25-0097e21a27da
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=96a5951d-94e2-4aea-9e25-0097e21a27da ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		96a5951d-94e2-4aea-9e25-0097e21a27da
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by Wayne_V on 2009-04-23
menu.lst looks OK.   something must be failing during the new kernel install.  I would try:

In one console window:
$ sudo tail -f /var/log/{dmesg,apt/term.log,kern.log,messages,syslog} | tee myLogs.txt

In another console window:
$ script myConsole.txt
 $ sudo apt-get purge linux-image-2.6.27-11-generic
$ sudo apt-get update ; sudo apt-get dist-upgrade
$ exit

And then ^C the  tail in the first window and post myLog.txt and myConsole.txt

---

### Post by sdennie on 2009-04-23
If the old kernel boots then it could be a problem with how your initrd is being created as your new kernel installs and creates it.  In fact, that's exactly what it looks like to me.  Have you recently made any changes in /etc/initramfs-tools?

---

### Post by Wayne_V on 2009-04-23
Could this be your problem:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/290153](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/290153)

---

### Post by Cesaar on 2009-04-24
> **sdennie said:**
> If the old kernel boots then it could be a problem with how your initrd is being created as your new kernel installs and creates it.  In fact, that's exactly what it looks like to me.  Have you recently made any changes in /etc/initramfs-tools?
No, I do not remember touching any of /etc/initramfs-tools. :/


> **Wayne_V said:**
> menu.lst looks OK.   something must be failing during the new kernel install.  I would try:

In one console window:
$ sudo tail -f /var/log/{dmesg,apt/term.log,kern.log,messages,syslog} | tee myLogs.txt

In another console window:
$ script myConsole.txt
 $ sudo apt-get purge linux-image-2.6.27-11-generic
$ sudo apt-get update ; sudo apt-get dist-upgrade
$ exit

And then ^C the  tail in the first window and post myLog.txt and myConsole.txt

Ok so I hope I did it right. I attached myLog.txt and myConsole.txt. I had problems uploading myConsole.txt so I had to put in a .zip file because apparently .txt files can only be <19.5Kb

I will now paste the tail from the first window:
```
cesar@cesar-laptop:~$ sudo tail -f /var/log/{dmesg,apt/term.log,kern.log,messages,syslog} | tee myLogs.txt
[sudo] password for cesar: 
==> /var/log/dmesg <==
[   22.112895] usbcore: registered new interface driver usbserial_generic
[   22.112898] usbserial: USB Serial Driver core
[   22.428617] EXT3 FS on sda1, internal journal
[   22.665895] usbcore: usbfs: unrecognised mount option "devmonde=0660" or missing value
[   22.665898] 
[   22.665902] usbcore: usbfs: mount parameter error:
[   22.956819] type=1505 audit(1240615986.081:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3980
[   23.197770] type=1505 audit(1240615986.321:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3985
[   23.198044] type=1505 audit(1240615986.321:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3985
[   23.435354] ip_tables: (C) 2000-2006 Netfilter Core Team

==> /var/log/apt/term.log <==
Setting up firefox-3.0 (3.0.9+nobinonly-0ubuntu0.8.10.1) ...
Please restart all running instances of firefox-3.0, or you will experience problems.

Setting up firefox-3.0-gnome-support (3.0.9+nobinonly-0ubuntu0.8.10.1) ...

Setting up firefox (3.0.9+nobinonly-0ubuntu0.8.10.1) ...
Setting up firefox-gnome-support (3.0.9+nobinonly-0ubuntu0.8.10.1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Log ended: 2009-04-23  10:53:09

==> /var/log/kern.log <==
Apr 24 18:38:52 cesar-laptop kernel: [  369.641596] wlan0: authenticated
Apr 24 18:38:52 cesar-laptop kernel: [  369.641606] wlan0: associate with AP 00:11:92:b0:0e:e1
Apr 24 18:38:52 cesar-laptop kernel: [  369.644183] wlan0: RX ReassocResp from 00:11:92:b0:0e:e1 (capab=0x431 status=0 aid=75)
Apr 24 18:38:52 cesar-laptop kernel: [  369.644191] wlan0: associated
Apr 24 18:39:44 cesar-laptop kernel: [  421.402295] wlan0: authenticate with AP 00:22:0c:26:a1:41
Apr 24 18:39:44 cesar-laptop kernel: [  421.404745] wlan0: authenticate with AP 00:22:0c:26:a1:41
Apr 24 18:39:44 cesar-laptop kernel: [  421.419286] wlan0: authenticated
Apr 24 18:39:44 cesar-laptop kernel: [  421.419294] wlan0: associate with AP 00:22:0c:26:a1:41
Apr 24 18:39:44 cesar-laptop kernel: [  421.423787] wlan0: RX ReassocResp from 00:22:0c:26:a1:41 (capab=0x431 status=0 aid=26)
Apr 24 18:39:44 cesar-laptop kernel: [  421.423795] wlan0: associated

==> /var/log/messages <==
Apr 24 18:33:21 cesar-laptop kernel: [   38.027928] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr 24 18:33:21 cesar-laptop kernel: [   38.030608] [drm] Initialized i915 1.6.0 20060119 on minor 0
Apr 24 18:33:21 cesar-laptop kernel: [   38.150409] Registered led device: iwl-phy0:radio
Apr 24 18:33:21 cesar-laptop kernel: [   38.150748] Registered led device: iwl-phy0:assoc
Apr 24 18:33:21 cesar-laptop kernel: [   38.150978] Registered led device: iwl-phy0:RX
Apr 24 18:33:21 cesar-laptop kernel: [   38.151187] Registered led device: iwl-phy0:TX
Apr 24 18:33:21 cesar-laptop kernel: [   38.161276] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 24 18:33:21 cesar-laptop kernel: [   38.290492] NET: Registered protocol family 17
Apr 24 18:33:24 cesar-laptop kernel: [   41.061703] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Apr 24 18:34:12 cesar-laptop kernel: [   89.230820] padlock: VIA PadLock not detected.

==> /var/log/syslog <==
Apr 24 18:39:44 cesar-laptop kernel: [  421.404745] wlan0: authenticate with AP 00:22:0c:26:a1:41
Apr 24 18:39:44 cesar-laptop kernel: [  421.419286] wlan0: authenticated
Apr 24 18:39:44 cesar-laptop kernel: [  421.419294] wlan0: associate with AP 00:22:0c:26:a1:41
Apr 24 18:39:44 cesar-laptop kernel: [  421.423787] wlan0: RX ReassocResp from 00:22:0c:26:a1:41 (capab=0x431 status=0 aid=26)
Apr 24 18:39:44 cesar-laptop kernel: [  421.423795] wlan0: associated
Apr 24 18:39:44 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 4 
Apr 24 18:39:44 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 5 
Apr 24 18:39:44 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 6 
Apr 24 18:39:44 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 6 -> 7 
Apr 24 18:39:47 cesar-laptop NetworkManager: <debug> [1240616387.202075] periodic_update(): Roamed from BSSID 00:11:92:B0:0E:E1 (restricted.utexas.edu) to 00:22:0C:26:A1:41 (restricted.utexas.edu) 
Apr 24 18:42:21 cesar-laptop ntpd[6468]: synchronized to 91.189.94.4, stratum 2
Apr 24 18:42:21 cesar-laptop ntpd[6468]: kernel time sync status change 0001

==> /var/log/apt/term.log <==

Log started: 2009-04-24  18:42:54
(Reading database ... 193778 files and directories currently installed.)
Removing linux-image-2.6.27-11-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms
Uninstalling: vboxdrv 2.0.4 (2.6.27-11-generic) (i686)

-------- Uninstall Beginning --------
Module:  vboxdrv
Version: 2.0.4
Kernel:  2.6.27-11-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.27-11-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.
depmod......

DKMS: uninstall Completed.
run-parts: executing /etc/kernel/prerm.d/last-good-boot
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

The link /vmlinuz is a damaged link
Removing symbolic link vmlinuz 
 you may need to re-run your boot loader[grub]
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-2.6.27-11-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

rmdir: failed to remove `/lib/modules/2.6.27-11-generic': Directory not empty
Log ended: 2009-04-24  18:43:27

==> /var/log/syslog <==
Apr 24 18:46:44 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 3 

==> /var/log/kern.log <==
Apr 24 18:46:46 cesar-laptop kernel: [  843.802416] wlan0: deauthenticated
Apr 24 18:46:46 cesar-laptop kernel: [  843.807231] wlan0: authenticate with AP 00:11:92:b0:0e:e1
Apr 24 18:46:46 cesar-laptop kernel: [  843.809215] wlan0: authenticated
Apr 24 18:46:46 cesar-laptop kernel: [  843.809223] wlan0: associate with AP 00:11:92:b0:0e:e1
Apr 24 18:46:46 cesar-laptop kernel: [  843.815980] wlan0: RX ReassocResp from 00:11:92:b0:0e:e1 (capab=0x431 status=0 aid=78)
Apr 24 18:46:46 cesar-laptop kernel: [  843.815987] wlan0: associated

==> /var/log/syslog <==
Apr 24 18:46:46 cesar-laptop kernel: [  843.802416] wlan0: deauthenticated
Apr 24 18:46:46 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 0 
Apr 24 18:46:46 cesar-laptop kernel: [  843.807231] wlan0: authenticate with AP 00:11:92:b0:0e:e1
Apr 24 18:46:46 cesar-laptop kernel: [  843.809215] wlan0: authenticated
Apr 24 18:46:46 cesar-laptop kernel: [  843.809223] wlan0: associate with AP 00:11:92:b0:0e:e1
Apr 24 18:46:46 cesar-laptop kernel: [  843.815980] wlan0: RX ReassocResp from 00:11:92:b0:0e:e1 (capab=0x431 status=0 aid=78)
Apr 24 18:46:46 cesar-laptop kernel: [  843.815987] wlan0: associated
Apr 24 18:46:46 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 4 
Apr 24 18:46:47 cesar-laptop NetworkManager: <debug> [1240616807.442046] periodic_update(): Roamed from BSSID 00:22:0C:26:A1:41 (restricted.utexas.edu) to 00:11:92:B0:0E:E1 (restricted.utexas.edu) 
Apr 24 18:46:47 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 5 
Apr 24 18:46:47 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 6 
Apr 24 18:46:47 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 6 -> 7 
Apr 24 18:49:45 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 5 
Apr 24 18:49:45 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 6 
Apr 24 18:49:45 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 6 -> 7 
Apr 24 18:52:42 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 3 

==> /var/log/kern.log <==
Apr 24 18:52:44 cesar-laptop kernel: [ 1201.589912] wlan0: deauthenticated
Apr 24 18:52:44 cesar-laptop kernel: [ 1201.595320] wlan0: authenticate with AP 00:11:92:b0:0e:e1
Apr 24 18:52:44 cesar-laptop kernel: [ 1201.596873] wlan0: authenticate with AP 00:11:92:b0:0e:e1
Apr 24 18:52:44 cesar-laptop kernel: [ 1201.599276] wlan0: authenticate with AP 00:11:92:b0:0e:e1
Apr 24 18:52:44 cesar-laptop kernel: [ 1201.603479] wlan0: authenticated
Apr 24 18:52:44 cesar-laptop kernel: [ 1201.603487] wlan0: associate with AP 00:11:92:b0:0e:e1
Apr 24 18:52:44 cesar-laptop kernel: [ 1201.609740] wlan0: RX ReassocResp from 00:11:92:b0:0e:e1 (capab=0x431 status=0 aid=78)
Apr 24 18:52:44 cesar-laptop kernel: [ 1201.609748] wlan0: associated

==> /var/log/syslog <==
Apr 24 18:52:44 cesar-laptop kernel: [ 1201.589912] wlan0: deauthenticated
Apr 24 18:52:44 cesar-laptop kernel: [ 1201.595320] wlan0: authenticate with AP 00:11:92:b0:0e:e1
Apr 24 18:52:44 cesar-laptop kernel: [ 1201.596873] wlan0: authenticate with AP 00:11:92:b0:0e:e1
Apr 24 18:52:44 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 0 
Apr 24 18:52:44 cesar-laptop kernel: [ 1201.599276] wlan0: authenticate with AP 00:11:92:b0:0e:e1
Apr 24 18:52:44 cesar-laptop kernel: [ 1201.603479] wlan0: authenticated
Apr 24 18:52:44 cesar-laptop kernel: [ 1201.603487] wlan0: associate with AP 00:11:92:b0:0e:e1
Apr 24 18:52:44 cesar-laptop kernel: [ 1201.609740] wlan0: RX ReassocResp from 00:11:92:b0:0e:e1 (capab=0x431 status=0 aid=78)
Apr 24 18:52:44 cesar-laptop kernel: [ 1201.609748] wlan0: associated
Apr 24 18:52:44 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 4 
Apr 24 18:52:44 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 5 

==> /var/log/kern.log <==
Apr 24 18:52:47 cesar-laptop kernel: [ 1204.447850] wlan0: deauthenticated

==> /var/log/syslog <==
Apr 24 18:52:47 cesar-laptop kernel: [ 1204.447850] wlan0: deauthenticated
Apr 24 18:52:47 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 0 
Apr 24 18:52:47 cesar-laptop NetworkManager: <debug> [1240617167.589916] periodic_update(): Roamed from BSSID 00:11:92:B0:0E:E1 (restricted.utexas.edu) to (none) ((none)) 
Apr 24 18:52:47 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 

==> /var/log/kern.log <==
Apr 24 18:52:48 cesar-laptop kernel: [ 1205.444070] wlan0: authenticate with AP 00:11:92:b0:0e:e1
Apr 24 18:52:48 cesar-laptop kernel: [ 1205.460121] wlan0: authenticated
Apr 24 18:52:48 cesar-laptop kernel: [ 1205.460130] wlan0: associate with AP 00:11:92:b0:0e:e1
Apr 24 18:52:48 cesar-laptop kernel: [ 1205.465227] wlan0: RX ReassocResp from 00:11:92:b0:0e:e1 (capab=0x431 status=0 aid=78)
Apr 24 18:52:48 cesar-laptop kernel: [ 1205.465235] wlan0: associated

==> /var/log/syslog <==
Apr 24 18:52:48 cesar-laptop kernel: [ 1205.444070] wlan0: authenticate with AP 00:11:92:b0:0e:e1
Apr 24 18:52:48 cesar-laptop kernel: [ 1205.460121] wlan0: authenticated
Apr 24 18:52:48 cesar-laptop kernel: [ 1205.460130] wlan0: associate with AP 00:11:92:b0:0e:e1
Apr 24 18:52:48 cesar-laptop kernel: [ 1205.465227] wlan0: RX ReassocResp from 00:11:92:b0:0e:e1 (capab=0x431 status=0 aid=78)
Apr 24 18:52:48 cesar-laptop kernel: [ 1205.465235] wlan0: associated
Apr 24 18:52:48 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 4 
Apr 24 18:52:48 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 5 
Apr 24 18:52:48 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 6 
Apr 24 18:52:48 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 6 -> 7 
Apr 24 18:52:49 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 5 
Apr 24 18:52:49 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 6 
Apr 24 18:52:49 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 6 -> 7 
Apr 24 18:52:50 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 5 
Apr 24 18:52:50 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 6 
Apr 24 18:52:50 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 6 -> 7 

==> /var/log/kern.log <==
Apr 24 18:52:51 cesar-laptop kernel: [ 1208.447852] wlan0: deauthenticated

==> /var/log/syslog <==
Apr 24 18:52:51 cesar-laptop kernel: [ 1208.447852] wlan0: deauthenticated
Apr 24 18:52:51 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 0 
Apr 24 18:52:51 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 

==> /var/log/kern.log <==
Apr 24 18:52:52 cesar-laptop kernel: [ 1209.444069] wlan0: authenticate with AP 00:11:92:b0:0e:e1
Apr 24 18:52:52 cesar-laptop kernel: [ 1209.446864] wlan0: authenticated
Apr 24 18:52:52 cesar-laptop kernel: [ 1209.446872] wlan0: associate with AP 00:11:92:b0:0e:e1
Apr 24 18:52:52 cesar-laptop kernel: [ 1209.449778] wlan0: RX ReassocResp from 00:11:92:b0:0e:e1 (capab=0x431 status=0 aid=78)
Apr 24 18:52:52 cesar-laptop kernel: [ 1209.449786] wlan0: associated

==> /var/log/syslog <==
Apr 24 18:52:52 cesar-laptop kernel: [ 1209.444069] wlan0: authenticate with AP 00:11:92:b0:0e:e1
Apr 24 18:52:52 cesar-laptop kernel: [ 1209.446864] wlan0: authenticated
Apr 24 18:52:52 cesar-laptop kernel: [ 1209.446872] wlan0: associate with AP 00:11:92:b0:0e:e1
Apr 24 18:52:52 cesar-laptop kernel: [ 1209.449778] wlan0: RX ReassocResp from 00:11:92:b0:0e:e1 (capab=0x431 status=0 aid=78)
Apr 24 18:52:52 cesar-laptop kernel: [ 1209.449786] wlan0: associated
Apr 24 18:52:52 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 4 
Apr 24 18:52:52 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 5 
Apr 24 18:52:53 cesar-laptop NetworkManager: <debug> [1240617173.594023] periodic_update(): Roamed from BSSID (none) ((none)) to 00:11:92:B0:0E:E1 (restricted.utexas.edu) 

==> /var/log/kern.log <==
Apr 24 18:52:55 cesar-laptop kernel: [ 1212.447885] wlan0: deauthenticated

==> /var/log/syslog <==
Apr 24 18:52:55 cesar-laptop kernel: [ 1212.447885] wlan0: deauthenticated
Apr 24 18:52:55 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 0 
Apr 24 18:52:55 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 

==> /var/log/kern.log <==
Apr 24 18:52:56 cesar-laptop kernel: [ 1213.444052] wlan0: authenticate with AP 00:11:92:b0:0e:e1
Apr 24 18:52:56 cesar-laptop kernel: [ 1213.446156] wlan0: authenticated
Apr 24 18:52:56 cesar-laptop kernel: [ 1213.446164] wlan0: associate with AP 00:11:92:b0:0e:e1
Apr 24 18:52:56 cesar-laptop kernel: [ 1213.448722] wlan0: RX ReassocResp from 00:11:92:b0:0e:e1 (capab=0x431 status=0 aid=78)
Apr 24 18:52:56 cesar-laptop kernel: [ 1213.448731] wlan0: associated

==> /var/log/syslog <==
Apr 24 18:52:56 cesar-laptop kernel: [ 1213.444052] wlan0: authenticate with AP 00:11:92:b0:0e:e1
Apr 24 18:52:56 cesar-laptop kernel: [ 1213.446156] wlan0: authenticated
Apr 24 18:52:56 cesar-laptop kernel: [ 1213.446164] wlan0: associate with AP 00:11:92:b0:0e:e1
Apr 24 18:52:56 cesar-laptop kernel: [ 1213.448722] wlan0: RX ReassocResp from 00:11:92:b0:0e:e1 (capab=0x431 status=0 aid=78)
Apr 24 18:52:56 cesar-laptop kernel: [ 1213.448731] wlan0: associated
Apr 24 18:52:56 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 4 
Apr 24 18:52:56 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 5 
Apr 24 18:52:56 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 6 
Apr 24 18:52:56 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 6 -> 7 

==> /var/log/messages <==
Apr 24 18:53:07 cesar-laptop -- MARK --

==> /var/log/syslog <==
Apr 24 19:01:18 cesar-laptop dhclient: DHCPREQUEST of 128.62.129.215 on wlan0 to 1.1.1.1 port 67
Apr 24 19:01:18 cesar-laptop dhclient: DHCPACK of 128.62.129.215 from 1.1.1.1
Apr 24 19:01:18 cesar-laptop NetworkManager: <info>  DHCP: device wlan0 state changed bound -> renew 
Apr 24 19:01:18 cesar-laptop NetworkManager: <info>    address 128.62.129.215 
Apr 24 19:01:18 cesar-laptop NetworkManager: <info>    prefix 23 (255.255.254.0) 
Apr 24 19:01:18 cesar-laptop NetworkManager: <info>    gateway 128.62.128.1 
Apr 24 19:01:18 cesar-laptop NetworkManager: <info>    nameserver '128.83.185.41' 
Apr 24 19:01:18 cesar-laptop NetworkManager: <info>    nameserver '128.83.185.40' 
Apr 24 19:01:18 cesar-laptop NetworkManager: <info>    domain name 'public.utexas.edu' 
Apr 24 19:01:18 cesar-laptop avahi-daemon[4559]: Withdrawing address record for 128.62.129.215 on wlan0.
Apr 24 19:01:18 cesar-laptop avahi-daemon[4559]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 128.62.129.215.
Apr 24 19:01:18 cesar-laptop avahi-daemon[4559]: Interface wlan0.IPv4 no longer relevant for mDNS.
Apr 24 19:01:18 cesar-laptop avahi-daemon[4559]: Joining mDNS multicast group on interface wlan0.IPv4 with address 128.62.129.215.
Apr 24 19:01:18 cesar-laptop avahi-daemon[4559]: New relevant interface wlan0.IPv4 for mDNS.
Apr 24 19:01:18 cesar-laptop avahi-daemon[4559]: Registering new address record for 128.62.129.215 on wlan0.IPv4.
Apr 24 19:01:18 cesar-laptop dhclient: bound to 128.62.129.215 -- renewal in 1672 seconds.
Apr 24 19:01:19 cesar-laptop NetworkManager: <info>  Policy set 'Auto restricted.utexas.edu' (wlan0) as default for routing and DNS. 
Apr 24 19:04:45 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 5 
Apr 24 19:04:45 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 6 
Apr 24 19:04:45 cesar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 6 -> 7 
```

To your second suggestion I will take a look right now and see if that is the problem. Thanks so much.

---

### Post by sdennie on 2009-04-24
I still think it's probably an initrd problem.  I don't know how to fix it but, to me, that error message means that either your filesystem or disk drivers don't exist in initrd and so you can't mount the root filesystem.  Those are the kinds of things that happen when you have that problem.  If another kernel boots with the same grub settings (which they appear to be) then, it points strongly at initrd.

---

### Post by Cesaar on 2009-05-28
The problem was solved after upgrading to Ubuntu 9.04. Thank you to everyone that tried to help! I love you!

---

