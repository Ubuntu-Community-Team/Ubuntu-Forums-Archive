---
title: "graphical filesharing between Ubuntu and OSX?"
date: 2006-01-01
forum: Desktop Environments
---

### Post by rainbowjoshua on 2006-01-01
As the subject implies, we are windows free here, but the only way I've found so far to share files with a graphical interface between the two is with samba and "windows file sharing" on the Mac.  While this technically works, the connection is incredibly slow (over our otherwise quite fast 100% signal strength wireless network).  Too slow to stream an mp3, let alone a movie, which will play, but stop to buffer every few seconds.

So there's got to be a better way, or there's got to be a way to make samba actually work reasonably.  Any ideas?  :)

Joshua

---

### Post by rklauco on 2006-01-01
[QUOTE=rainbowjoshua]While this technically works, the connection is incredibly slow (over our otherwise quite fast 100% signal strength wireless network).  Too slow to stream an mp3, let alone a movie, which will play, but stop to buffer every few seconds.[/QUOTE]
Interesting.
Are you sure you have no problem with the samba/network settings?
Try some FTP and test the transfer rate.
I have nfs enabled on Ubuntu along with samba.
Both connections work great from ubuntu machine, samba is working from windows machines too and the transfer rate is arount 8MB/s, wich hits the ethernet limit at my location.
The DVD movies (not mentioning the DiVX) are playable also using old wifi usb dongle (11Mbps) on my laptop with WinXP, so your transfer rate must be less than that.
AFAIK OS X is *nix, so it should be able to work as NFS server/client.

---

