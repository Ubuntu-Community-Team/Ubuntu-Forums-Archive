---
title: "Ubuntu/xp dual boot problem"
date: 2008-11-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Gopargur on 2008-11-30
I've owned my dell Inspiron E1505 for close to 3 years now.  A couple months ago I decieded to dual boot my computer with Ubuntu.

Now for some reason on the boot menu, it keeps adding more boot spots for Ubuntu.

Ex.
At first started off just showing the option to boot
Ubuntu
Ubuntu Troubleshooting mode
Microsoft XP

A week later shows the option to boot
Ubuntu
Ubuntu Troubleshooting mode
Ubuntu
Ubuntu Troubleshooting mode
Microsoft XP

Now:
Ubuntu
Ubuntu Troubleshooting mode
Ubuntu
Ubuntu Troubleshooting mode
Ubuntu
Ubuntu Troubleshooting mode
Microsoft XP

Anyone know why it keeps adding the option to boot ubuntu more times?  All these boot up correctly, just not sure why it shows up on the list more than just once

---

### Post by alan34 on 2008-12-01
A hopefully quick explanation.

When a updated Linux kernel is installed - normally through the update manager your grub file is rewritten with the new Linux kernel in the file.

However the older kernels are not removed so your grub listing when you boot up just gets longer and longer. This is not so bad a thing as it gives you the option of going back to an older Linux kernel if any of your hardware does not work with the latest version of the kernel.

Go System - Administration - System Monitor then click the System tab and you will see something like

Ubuntu
Release 8.10 (intrepid)
Kernel Linux 2.6.27-10-generic


The 2.6.27-10 is the important part which if you look is on your grub menu.

Two ways to "get rid" of the older versions. First write down which ones are the older versions, then

Either comment out the versions in your grub menu file like so

Go Applications - Accessories - Terminal

then type

sudo cp /boot/grub/menu.lst /boot/grub/menu.backup_1_12_2008
gksudo gedit /boot/grub/menu.lst

and put a # in front of the kernel(s) you do not want and save the file.

for example
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
# title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode) (on /dev/sda8)
# root		(hd0,7)
# kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=009596c1-e588-
490e-ae8d-7668470f1998 ro single 
# initrd		/boot/initrd.img-2.6.24-18-generic
# savedefault
# boot


Or go System - Administration - Synaptic Package Manager

Search for 2.6.27 and remove all the old kernel(s) and your grub menu file will be updated. There will be 3 or 4 files to remove for each kernel (right click to select remove). Just make sure you do NOT remove ALL the kernels or boy are you in trouble.

The first way is dead safe but the second way is fine just take your time
and be a bit careful.

Hope this helps you and sorry it is so long :)

---

### Post by Gopargur on 2008-12-02
Thanks Alan.

That cleared everything up for me.  I had a feeling that it could be because of new versions, but wasn't quite sure.

---

