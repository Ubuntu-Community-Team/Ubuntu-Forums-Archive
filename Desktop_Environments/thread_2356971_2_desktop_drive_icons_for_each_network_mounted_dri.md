---
title: "2 desktop drive icons for each network mounted drive"
date: 2017-03-28
forum: Desktop Environments
---

### Post by Aero_Nexcom on 2017-03-28
I am on a dell xps-15 laptop, upgraded to 16.10 booting classic gnome and using nemo. Drives are mounted from fstab. If I mount using sudo mount -a when no drives are mounted, I get a single icon for each mounted (from a samba server [16.04] on local network) drive. I on the other hand when I reboot, I get 2 icons for each mounted network drive. local drive (hard disk partition) has only single icon at any time.

I am using systemd mounting method as shown below (only showing 1 for brevity):
//LINUX-SERVER/bee_dsk2/ /media/bee_dsk2/ cifs nodev,noexec,nouser,rw,nofail,x-systemd.automount,x-systemd.requires=network-online.target,credentials=/root/.smbfscredentials 0 0

I have tried many variants but all were unsuccessful at fixing the multiple ICONS issue.
I have tried with both unity and gnome (my default) but it is the same in both.
when I look at nemo (or nautilus) it shows that they are mounted both under devices and under network.

if I do sudo umount -a followed by sudo mount -a, then they are all mounted under Network and the only thing listed under Devices is the windows partition on my hard disk.

Have looked many times on the net but have not found a solution. Does anyone have a hint what I have done wrong?

thanks

---

### Post by beerhat on 2017-04-11
Same behavior here but on Mint 18.1 MATE.  Driving me absolutely bonkers.  I have 6 NFS mounts and, well 12 icons on the desktop.  6 are drive icons, the duplicates are folder-like icons.  Any thoughts?  Never had mount issues before this latest version and now this.. and the dbus/wifi shutdown delay condition.  argh.

---

