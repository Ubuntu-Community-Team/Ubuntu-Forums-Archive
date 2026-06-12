---
title: "Auto Shutdowns and Torrent problems"
date: 2009-06-22
forum: General Help
---

### Post by Waisybabu on 2009-06-22
This absolutely PISSES me off in Ubuntu: It shuts down randomly for no god-damn reason. 

The shut-down does go smoothly but in the process, it takes away the torrent I was downloading at the time.

Whenever I use Transmission to get a torrent and if the computer goes off (this has happened twice since I installed it), POOF! the torrent's gone! This didn't happen with uTorrent!

These shutdowns usually happen when the laptop is a bit hotter than it's supposed to be. But then again, Windows XP ignored this aspect and never turned off like this and even if it *did,* it would save my torrents from going back to 0%

And FYI: I use a 2003 Sony VAIO VGN-A19GP.

---

### Post by lovinglinux on 2009-06-22
When you restart the torrent is not listed in Transmission anymore or it simply starts from 0%? If it vanishes, then you could download the .torrent again and force a recheck. Have you checked if the actual file the .torrent downloads it still in the download folder?

There are [some reports](http://ubuntuforums.org/showthread.php?t=1030841) about permission issues with Transmission that could this.

Are you using ext4?

Ext4 uses delayed allocation, so if the computer restarts abruptly, you might loose data like torrents. Nevertheless, I had several power failures and never lost anything, including torrents. But I use Deluge. 

I personally would recommend using [Deluge](apt:deluge) [apt-get], which is much better than Transmission and even better than uTorrent IMO.

---

### Post by Waisybabu on 2009-06-23
> **lovinglinux said:**
> When you restart the torrent is not listed in Transmission anymore or it simply starts from 0%? If it vanishes, then you could download the .torrent again and force a recheck. Have you checked if the actual file the .torrent downloads it still in the download folder?

There are [some reports](http://ubuntuforums.org/showthread.php?t=1030841) about permission issues with Transmission that could this.

Are you using ext4?

Ext4 uses delayed allocation, so if the computer restarts abruptly, you might loose data like torrents. Nevertheless, I had several power failures and never lost anything, including torrents. But I use Deluge. 

I personally would recommend using [Deluge](apt:deluge) [apt-get], which is much better than Transmission and even better than uTorrent IMO.

[Reason(s) I left Ubuntu to try on a later date.]("http://sarcasticgamer.com/forums/showthread.php?t=21435")

---

### Post by aeiah on 2009-06-23
you should be able to set a behavior for what happens when the computer gets too hot, and at what temperature is deemed too hot. perhaps set it to the same threshold that exists in windows.

but yes, are you saying that downloaded data is actually missing after a shutdown? its not a case that you previously used a download location different to the default, and transmission reverts back to this default, hence starting at 0%? 

perhaps try deluge. i prefer it and a lot of other people do too

---

### Post by lovinglinux on 2009-06-23
Also try dual-booting instead of using Wubi.

---

### Post by Waisybabu on 2009-06-24
> **lovinglinux said:**
> Also try dual-booting instead of using Wubi.

That and using Deluge is what I will do once I get an external hard drive to back up and get rid of the redundant files on my laptop. 60GB isn't really that much after all! 

And yes, the download *status* goes back to 0%

---

