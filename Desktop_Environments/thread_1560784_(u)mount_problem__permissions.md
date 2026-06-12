---
title: "(u)mount problem / permissions"
date: 2010-08-25
forum: Desktop Environments
---

### Post by dubbaluga on 2010-08-25
Hi,

I am using XFCE 4.6.2 with thunar 1.0.2-1+b1. 

When mounting a USB-stick with a vfat filesystem in thunar I can access the contents read-only. Creating files only works with applications running with root privileges and unmounting as a normal user does not work as well:
```

Failed to unmount "USB_STICK_0"
The volume "USB_STICK_0" was probably mounted manually on the command line.

```
The usb-stick has not been mounted in a shell and this message is shown as a messagebox. Has anyone a clue how to fix this? Preferably no [FONT="Fixedsys"]/etc/fstab[/FONT] modification hacks, maybe by using [FONT="Fixedsys"]gconf-editor[/FONT] properly or configuring HAL.

Thanks in advance,
  Rainer

---

### Post by quixote on 2010-08-27
I haven't used thunar. (I was involuntarily sucked off into gnome a few years back. Long story.)  But I'm assuming it's something like nautilus, where it shows the unmounted drives, and when you click on one, it mounts it.  Is that right?

Again, I don't know how it works in thunar, but in nautilus trying to change its defaults is megahairy.  The easiest solution is to edit fstab.  Really.  (There's nothing in gconf-editor, afaik, and I wouldn't even think of editing HAL.)

An added wrinkle is that Lucid wants the drive identified by UUID, which means an fstab entry for a specific USB stick is easy, but a generic one for all USB sticks I'm not sure how you would do that. Possibly, the old standby of just using eg /dev/sdb1 would still work.

1)  Find the uuid:```
sudo blkid
```that will return the uuid's of all partitions on your system.  Find the one for your usb stick, which will probably be listed as something like /dev/sdb1. Highlight the uuid with the mouse, and use ctrl-shift-c to copy it. In step 3 you can use ctrl-v to copy the whole string where it belongs.

2) Make a directory where you will be mounting the USB-stick, eg /media/usb_stick_0

3) Open /etc/fstab as root: ```
gksu gedit /etc/fstab
```and append these lines```
#a comment if you want to describe the entry, eg 8GB Transcend USB stick
UUID=long-alphanumeric-string   /media/usb_stick_0  vfat noauto,user,dmask=022,fmask=133  0  0
```
What that line says is:
[LIST]
[*]which device to mount, 
[*]then the mount point, 
[*]then the type of filesystem (I'm assuming vfat, if you know it's something else, substitute the right filesystem designation, eg ext2, or whatever)
[*]then the all-important options: do not try to mount at boot, allow users to mount and unmount not just root, and apply 755 permissions to directories, and 644 permissions to files.  The final two zeroes tell the system not to do filesystem checks or backup automatically.
[/LIST]
If you want the same permissions on files and dirs, you could use umask=022.  If you want all files readable and writable by anyone, you'd use umask=000.

---

