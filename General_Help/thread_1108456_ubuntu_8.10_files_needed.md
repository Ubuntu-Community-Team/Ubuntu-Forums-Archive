---
title: "ubuntu 8.10 files needed"
date: 2009-03-27
forum: General Help
---

### Post by pooh_bear on 2009-03-27
Hi all, I'm new here. I tried to download 8.10 intrepid, but 5 of the files didn't checksum. If anyone could be so kind to post these files from your ubuntu-8.10-alternate-i386.iso CD, I would appreciate it. Alternatively, it would be cool to know where I could get these, whatever's easier.

.\install\netboot\pxelinux.cfg\default

.\install\netboot\ubuntu-installer\i386\initrd.gz

.\install\netboot\pxelinux.0

.\pool\main\x\xserver-xorg-video-ati\xserver-xorg-video-radeon_6.9.0+git20081003.f9826a56-0ubuntu2_i386.deb

.\pool\main\x\xserver-xorg-video-ati\xserver-xorg-video-ati_6.9.0+git20081003.f9826a56-0ubuntu2_i386.deb

Ryan

---

### Post by zvacet on 2009-03-28
Download same iso with torrent and point download to the folder where your existing iso is.Torrent will just check your iso and replace bad files with good ones.That way you don´t have to download ~ 700MB of files.After you do that run md5sum and if it is correct (it should be) burn iso and check CD integrity.If that is O.K. you are ready to install.

---

### Post by sekinto on 2009-03-28
I agree. I can't remember the last time I downloaded something big without using a BitTorrent program or some type of download manager. The BitTorrent protocol is extremely reliable (at least that is my experience).

---

### Post by hyper_ch on 2009-03-28
bittorrent will auto check the completed data. Maybe the downloaded image was fine but the burnt cd had an error. You might also want to check that.

Do a md5 check of the iso and compare it with the md5 checksum given by ubuntu.com

---

### Post by pooh_bear on 2009-03-28
Thanks guys, I didn't know about bit torrent replacing a bad file. But what's funny, is that I ran an md5 on the 1700 files in the iso (a good iso copy, I know it's good 'cause the checksum was right), and four were bad. Maybe someone can confirm this.

---

