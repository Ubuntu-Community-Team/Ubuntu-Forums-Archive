---
title: "Amule &amp; Bittorrent Issues"
date: 2007-08-17
forum: Gaming &amp; Leisure
---

### Post by leezer3 on 2007-08-17
Hiya,
Rather odd situation here, would appreciate it if someone could shed a little light or at least see something I've missed.
I've got a headless server here (Admined via VNC), which I'm using to run my downloads & serve files to the network. Specs-
> Athlon64 3000+
Epox Nforce 3 motherboard  (Can find the specs if anyone considers it important)
512mb RAM
20gb IDE Seagate, used for boot drive
4x 160gb drives (Two IDE & two SATA) split into 1x 320gb LVM & 2x 160gb data drives.
100mbs connection, running through the forcedeth driver. I've also tried a Realtek 100mbs PCI card with the same results.
20megs down, 768k up cable connection
Feisty 7.04 is the base install, but there's a lot of custom built & SVN stuff on there. 32bits, for stability reasons with some apps

Torrents are handled by the current SVN for QBittorrent & Emule is handled via the current Amule SVN. (I need the SVN for both of these for various features; I appreciate it may introduce odd problems, but as far as I can tell its not related to what I'm seeing)

Issues arise when I try to run both Amule & any torrent client at the same time- This totally kills the download speed for both programs, but not anything else. (I can browse & download via HTTP up to the limits of my connection quite happily)
Running each program on its own produces the download speeds I would expect, but together they grind to a halt at about 10kb/s download & max the upload.

So far, I've tried changing the torrent client (Azureus & Qbittorrent both have the same issues), limiting both the number of connections & the upload speed for both P2P programs & fiddling with every firewall script & similar I can think of. Nothing seems to change though- The speeds remain awful.
What really annoys me is that I can run the Windows equivalents of these two apps side by side with perfect download speeds (On Windows, I use uTorrent & Emule 0.48a), so its something in the setup of the Linux box.

Amule is the only component in the chain I haven't changed out, but I simply can't find a decent alternative, and I'm not sure it'd make any difference TBH.


Anyone with any thoughts or solutions please?

-Leezer-

---

