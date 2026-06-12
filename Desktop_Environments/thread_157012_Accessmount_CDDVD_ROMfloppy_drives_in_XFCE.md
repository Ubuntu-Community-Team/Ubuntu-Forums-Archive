---
title: "Access/mount CD/DVD ROM/floppy drives in XFCE"
date: 2006-04-08
forum: Desktop Environments
---

### Post by Ian Edmont on 2006-04-08
Hi,

Not sure if this is the correct group to ask this so please excuse me if it isn't.

Just installed Xubuntu Dapper Flight 6.

Can someone please explain how to access the CD/DVD ROM and floppy drives.

Fairly new to Linux so not sure where to start.

Many thank.

---

### Post by 5-HT on 2006-04-08
XFCE does not automount removable media (unless this has been changed for Dapper).

Two 'pure' options, and one hybrid (that automounts) are available:

1. GUI: XFCE fstab mount manager.

Just point and double-click on the device and it should mount.
To unmount, there should be an option if you right-click the device.

2. CLI: mount manually

e.g. for floppy (for CD, just replace 'floppy' with 'cdrom' or other according to the device):

To mount: ```
 mount /media/floppy 
``` To unmount: ```
 mount /media/floppy 
``` 
3. If you have GNOME installed:
 You could use 'gnome-volume-manager' to automatically mount removable media. 
To unmount, it can be done via nautilus, CLI, or possibly XFCE fstab mount manager.
To enable it, type ```
 gnome-volume-manager &  
``` in a terminal and save your XFCE session on logout.


*Note: Once mounted, you can browse the device using the terminal, or a file browser.
I think 'Thunar' is now the default for XFCE (it used to be 'rox'), you could always use nautilus if you have GNOME installed.

Hope this helps.

---

### Post by Ian Edmont on 2006-04-08
Thanks for the reply 5-HT.

Managed to manaully mount the floppy device but not cdrom.

Don't seem to have an option to launch XFCE fstab mount manager. Where would I find this?

Having trouble installing my Fujitsu ADSL FDX310 USB modem though now. Managed in Ubuntu and Kubuntu so need to try and get a fix for this too.

Once again, thanks.

---

