---
title: "Kubuntu usb/ipod autodetect doesn't quite work"
date: 2005-10-15
forum: Desktop Environments
---

### Post by Jengu on 2005-10-15
When I plug in my ipod, it gets mounted as two drives automatically, /media/ipod (which has the usual ipod files) and /media/sda2 (which is empty). Konqueror comes up automatically and tries to open media:/sdb1 and media:/sdb2 but can't find either. If I go to media:/ the ipod isn't listed at all, just my HDs, floppy and CD.

Any ideas for what's wrong? Should I file a bug?

---

### Post by Firetech on 2005-10-15
There are some issues with HAL (Hardware Abstraction Layer, the stuff that handles USB stuff etc.) in KDE right now. Updates are "pending", whatever that means...
It's a known issue, so you don't need to file a bug, yet...

---

### Post by paul cooke on 2005-10-15
would this be why my USB drives are seen by Gnome but I can't see them at all with KDE?

I get these outputs for these commands:
paulc@cooke-one:~$ lsmod | grep usb
usb_storage            64704  1
scsi_mod              124872  2 sd_mod,usb_storage
usbcore               104188  4 usb_storage,ehci_hcd,uhci_hcd
ide_core              125268  5 usb_storage,ide_cd,ide_disk,ide_generic,piix

and
paulc@cooke-one:~$ lsusb
Bus 005 Device 002: ID 0d49:7010 Maxtor
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

so as far as I can tell, the modules are there and the Maxtor drive has been seen, but the mount point doesn't exist in KDE

---

### Post by Asraniel on 2005-10-15
my ipod doesent get mounted at all.. nothing happens if i connect my ipod

---

### Post by ltmon on 2005-10-15
I just upgraded to Breezy, but with kde 3.5 beta.

iPod works fine in that case.  Even better than Hoary: I no longer get two drives on my desktop (just one) and it's name is the name of my iPod.  It even has an iPod icon :) :)

Now if only it would open with the "ipod:/" uri when I click on it... oh well at least it's now getting there.

L.

---

### Post by kLy on 2005-10-22
[QUOTE=Firetech]There are some issues with HAL (Hardware Abstraction Layer, the stuff that handles USB stuff etc.) in KDE right now. Updates are "pending", whatever that means...
It's a known issue, so you don't need to file a bug, yet...[/QUOTE]
Do you know what the bug number is for this issue is? I couldn't seem to find it in bugzilla. thx

---

### Post by Jengu on 2005-10-22
I did an apt-get update and apt-get upgrade a few days ago and it had a bunch of KDE updates that made the situation slightly better for me. The ipod actually mounts now, but it still opens multiple tabs and seems to mount multiple devices. Maybe I'll try 3.5 :)

---

### Post by aysiu on 2005-10-22
[QUOTE=kLy]Do you know what the bug number is for this issue is? I couldn't seem to find it in bugzilla. thx[/QUOTE] [http://www.ubuntuforums.org/showthread.php?t=74541](http://www.ubuntuforums.org/showthread.php?t=74541)

---

### Post by wd5iyt on 2005-12-26
My lovely wife bought me an Ipod Video for Christmas, and I've done some work with it.  I think I can answer a couple of questions about the automounting issue, at least in KDE 3.5.

There seems to be a conflict between ivman and the KDE hal interface.  My kubuntu system had ivman installed and it would automount USB devices.  This worked as expected with KDE 3.4, but when I upgraded to KDE 3.5, I started seeing "double" mounts.

I had seen this with USB keys and USB hard drives and never investigated the cause, but with the Ipod, it was annoying.  I looked into it further and found that indeed KDE 3.5 handles hal events differently than 3.4.

In order to get things to be consistent, you can either disable the KDE hal event processing in the "media" area of the system settings, or you can remove ivman (which is what I did) and let KDE handle it.

The only problem I'm having now is that while ivman would mount the Ipod as /media/ipod (it used the volume name), kde mounts it as /media/sda2, which is the device name instead of the volume name.  I have not figured this out yet, but it's only a minor inconvenience.

Also, the versions of gtkpod and libgpod in the Ubuntu repositories are not recent enough to handle the Ipod video files.  I got newer packages from here:  [http://www.badcow.homelinux.net/](http://www.badcow.homelinux.net/)

YMMV, but mine's working great now!

Jim

---

### Post by jetpeach on 2006-01-16
I have the same problems with my ipod video, but when I tried removing ivman synaptic says I must also remove Kubuntu-desktop!?  Also, I need to be able to access my ipod from a terminal (I run a script to sync my calendar to the Calendar directory) and only ivman mounts the ipod in /media/ipod where it is accessible by the terminal (is it possible to access system:/media from a bash terminal script? I haven't seen a way).

I updated my libgpod to 0.3.0, but it doesn't seem to help.
The link you posted is dead, did it have Deb packages at it?  I compiled and maked from the source files at [http://www.gtkpod.org/downloads.html]("http://www.gtkpod.org/downloads.html") but like I said it didn't improve the double mount problems.


[QUOTE=wd5iyt]
In order to get things to be consistent, you can either disable the KDE hal event processing in the "media" area of the system settings, or you can remove ivman (which is what I did) and let KDE handle it.

The only problem I'm having now is that while ivman would mount the Ipod as /media/ipod (it used the volume name), kde mounts it as /media/sda2, which is the device name instead of the volume name.  I have not figured this out yet, but it's only a minor inconvenience.

Also, the versions of gtkpod and libgpod in the Ubuntu repositories are not recent enough to handle the Ipod video files.  I got newer packages from here:  [http://www.badcow.homelinux.net/](http://www.badcow.homelinux.net/)

YMMV, but mine's working great now!

Jim[/QUOTE]

---

### Post by jetpeach on 2006-01-16
I have the same problems with my ipod video, but when I tried removing ivman synaptic says I must also remove Kubuntu-desktop!?  Also, I need to be able to access my ipod from a terminal (I run a script to sync my calendar to the Calendar directory) and only ivman mounts the ipod in /media/ipod where it is accessible by the terminal (is it possible to access system:/media from a bash terminal script? I haven't seen a way).

I updated my libgpod to 0.3.0, but it doesn't seem to help.
The link you posted is dead, did it have Deb packages at it?  I compiled and maked from the source files at [http://www.gtkpod.org/downloads.html]("http://www.gtkpod.org/downloads.html") but like I said it didn't improve the double mount problems.

I also tried disabling the HAL in KDE, but this seemed to make my scanner bomb :(  any advice is appreciated.
jet


[QUOTE=wd5iyt]
In order to get things to be consistent, you can either disable the KDE hal event processing in the "media" area of the system settings, or you can remove ivman (which is what I did) and let KDE handle it.

The only problem I'm having now is that while ivman would mount the Ipod as /media/ipod (it used the volume name), kde mounts it as /media/sda2, which is the device name instead of the volume name.  I have not figured this out yet, but it's only a minor inconvenience.

Also, the versions of gtkpod and libgpod in the Ubuntu repositories are not recent enough to handle the Ipod video files.  I got newer packages from here:  [http://www.badcow.homelinux.net/](http://www.badcow.homelinux.net/)

YMMV, but mine's working great now!

Jim[/QUOTE]

---

