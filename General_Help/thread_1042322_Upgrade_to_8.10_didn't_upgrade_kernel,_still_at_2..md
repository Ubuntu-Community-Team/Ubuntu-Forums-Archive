---
title: "Upgrade to 8.10 didn't upgrade kernel, still at 2.6.24-16-generic"
date: 2009-01-17
forum: General Help
---

### Post by mopi on 2009-01-17
As the title says. The upgrade to 8.10 didn't upgrade my kernel. Is there a reason for this? Perhaps related to nvidia drivers? How do I upgrade the kernel to latest? In synaptic it looks like it is installed.

---

### Post by gettinoriginal on 2009-01-17
```
sudo apt-get update && sudo apt-get dist-upgrade
```  :P

---

### Post by mopi on 2009-01-17
That didn't change anything.


0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by adult swim on 2009-01-17
post the results of ```
cat /boot/grub/menu.lst
```
run this ```
sudo update-grub
``` and then run the first command again.  paste them both back so we can compare them.

---

### Post by mopi on 2009-01-17
I think you are onto something.

Here is the result of update-grub:

```
johan@svarta:~$ sudo update-grub
[sudo] password for johan: 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-9-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

The content of /boot/grub/menu.lst were identical before and after update-grub. Now that you mention grub I remember that I had to manually configure which drive to should boot from in order to get 8.04 to boot initially. But I don't know what is the proper way to upgrade this.

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=2971d09e-d0f2-412a-b5c4-7fe4f1efc517 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2971d09e-d0f2-412a-b5c4-7fe4f1efc517 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2971d09e-d0f2-412a-b5c4-7fe4f1efc517 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by pastalavista on 2009-01-17
Open System>Administration>Software Resources and click the 'Updates' tab and be sure to select (at the bottom) "Normal Releases". Also be sure all the repositories are enabled. Then do 'sudo apt-get update' again

---

### Post by adult swim on 2009-01-17
hmm update grub should have updated your menu.lst but it didnt so we will have to do it manually.  if you upgraded from 8.04 to 8.10 then this should work. run ```
gksudo gedit /boot/grub/menu.lst
``` and make it look like this at the bottom
```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=2971d09e-d0f2-412a-b5c4-7fe4f1efc517 ro quiet splash
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=2971d09e-d0f2-412a-b5c4-7fe4f1efc517 ro single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2971d09e-d0f2-412a-b5c4-7fe4f1efc517 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2971d09e-d0f2-412a-b5c4-7fe4f1efc517 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```
then save and close the file.  the next time you reboot you should be able to boot the newer kernel 2.6.27-9

---

### Post by mopi on 2009-01-17
@pastalavista
It's selected. I'm running 8.10. It's just the kernel that wasn't upgraded.

@adult swim
That worked. Thanks!

I do remember now that I choose to keep the local menu.lst during the upgrade. I did that because I wanted to keep my settings to boot from my ide drive instead of my sata drive, something that was impossible for grub to respect without manual config back in 8.04. It didn't occur to me that I also was specifying a kernel version. Will I need to edit menu.lst every time a new kernel is downloaded from the repos in order to use it now?

---

### Post by jocko on 2009-01-17
> **mopi said:**
> Will I need to edit menu.lst every time a new kernel is downloaded from the repos in order to use it now?

Maybe/maybe not... but I came up with a way to get update-grub to make a completely new menu.lst (read [this post]("http://ubuntuforums.org/showpost.php?p=6559591&postcount=25")). I'm pretty sure it will work in your case, and it will make sure new kernels are added to the menu in the future.

> **mopi said:**
> I did that because I wanted to keep my settings to boot from my ide drive instead of my sata drive, something that was impossible for grub to respect without manual config back in 8.04.
Check for this section in menu.lst:
```
## default grub root device
## e.g. groot=(hd0,0)
[COLOR=Blue]# groot=(hd0,0)[/COLOR]
```Set it to the correct drive/partition (i.e. (hd1,0) if ubuntu is on the first partition of your second hard drive). This is where update-grub gets the value for the "root" line in the menu, so if it's set wrong, the menu will be updated to the wrong root device every time update-grub is run.

---

### Post by mopi on 2009-01-17
Thanks jocko.

I removed the old menu.lst and regenerated a new. The new file does not contain any root line. But it works anyway. Grub boots from the correct drive. This was not the case with 8.04 so probably grub has been updated/fixed.

---

