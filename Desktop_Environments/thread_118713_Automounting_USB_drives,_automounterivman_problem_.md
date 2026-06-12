---
title: "Automounting USB drives, automounter/ivman problem from Breezy upgrade"
date: 2006-01-17
forum: Desktop Environments
---

### Post by Jimmy The Clown on 2006-01-17
All-

I have been having problems with external USB drives on my breezy install for sometime. I think it started after I upgraded from hoary to breezy with a "dist-upgrade" back in October.

When I attach an external drive I get no friendly icon on my desktop or any other happiness. Sometimes a new Nautilus window opens showing the drive for an instant and then the drive disconnects and the window switches to something generic.

lsusb does not show the device as connected. Another really strange thing that is probably related is that on shut down I always receive an error message about trying to stop the ivman.pid but being unable to find it. This also started after upgrading to breezy.

I tried doing a full removal of both ivman and automounter in synaptic and then reinstalling them, but the error is still there and the automounter still doesn't work properly.

Anyone got any ideas? Thanks.

-JTC

EDIT: I just tried connecting my usb drive to a different usb port on my laptop (the one I always use for my mouse) and it mounted and played nice and everything. My mouse worked in the other 2 ports, so I guess this is a temporary solution, but it won't allow me to transfer files from one USB drive to another.

---

### Post by ranf on 2006-01-17
ivman is not installed by default Ubuntu. 
It is used when you install the package "xubuntu-desktop".

In pure Gnome the "gnome-volume-manager" is responsible for automounting.

---

### Post by Jimmy The Clown on 2006-01-17
I did migrate over to kubuntu-desktop but didn't like it and tried to delete all associated files that weren't needed by ubuntu-desktop, but that proved to be difficult.

My other post was a little premature I guess. Although my mp3 player (Archos Gmini) mounted fine on that USB port, my external hard drive didn't. I just downloaded the breezy livecd, so I am going to see if that works. Should help determine if it's an issue with my install or a hardware conflict in general. I will also try wiping any crazy confs that might exist for gnome-volume-manager by doing a complete removal and a reinstall. Thanks for the info.

-JTC

---

### Post by dcstar on 2006-01-17
[QUOTE=Jimmy The Clown]All-

I have been having problems with external USB drives on my breezy install for sometime. I think it started after I upgraded from hoary to breezy with a "dist-upgrade" back in October.
......
Anyone got any ideas? Thanks.

-JTC

EDIT: I just tried connecting my usb drive to a different usb port on my laptop (the one I always use for my mouse) and it mounted and played nice and everything. My mouse worked in the other 2 ports, so I guess this is a temporary solution, but it won't allow me to transfer files from one USB drive to another.[/QUOTE]
In a terminal, run "dmesg" when you plug things in (or load disks) to see what your system is doing for those events.

---

