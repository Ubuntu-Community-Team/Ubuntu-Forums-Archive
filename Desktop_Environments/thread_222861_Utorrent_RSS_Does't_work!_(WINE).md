---
title: "Utorrent RSS Does't work! (WINE)"
date: 2006-07-25
forum: Desktop Environments
---

### Post by truantology on 2006-07-25
Hey all,

Dapper Drake x86...
Running Wine 0.9.17 (configured with winetools)
I installed utorrent 1.60 from their website.  Everything works fine, but I can't for the life of me get the RSS Feeds to work.
I can add feeds, but when I double-click on a release, it comes up with an unvalid .torrent file error.  

What can I do to get this working?

Thanks,
TruANT

---

### Post by hikitsu4 on 2006-07-26
> **truantology said:**
> Hey all,

Dapper Drake x86...
Running Wine 0.9.17 (configured with winetools)
I installed utorrent 1.60 from their website.  Everything works fine, but I can't for the life of me get the RSS Feeds to work.
I can add feeds, but when I double-click on a release, it comes up with an unvalid .torrent file error.  

What can I do to get this working?

Thanks,
TruANT
It works for me i added "http://www.rpguru.com/rss.php" and pressed on a release and the download manager went up and i pressed ok, and it worked. 

Note: I followed my own guide when i installed wine with utorrent and using Xubuntu 6.06.

[http://www.ubuntuforums.org/showthread.php?t=191161](http://www.ubuntuforums.org/showthread.php?t=191161)

---

### Post by truantology on 2006-07-26
Wow, soo weird.  That link you gave worked for me.  But when I try to get something from my "Other" torrent groups, it says this:

Unable to load "somebittorrent download.torrent": Invalid torrent file!

Any ideas?

---

### Post by hikitsu4 on 2006-07-27
> **truantology said:**
> Wow, soo weird.  That link you gave worked for me.  But when I try to get something from my "Other" torrent groups, it says this:

Unable to load "somebittorrent download.torrent": Invalid torrent file!

Any ideas?
I "think" you just got the links wrong or something i tried two other anime bt sites, "http://www.baka-updates.com/rss.php" and "http://www.tokyotosho.com/rss.php", and it worked perfectly :p

The problem can "also" be that utorrent RSS doesn't support that RSS type i dont know.

---

### Post by truantology on 2006-07-27
damn, those work too!!  Thanks, hikitsu...well, I know it works with those sites, but still not with my two.
The Following Sites require authentication though, so I have to enter the link into RSS like this:
hxxp://www.************.net/rssdd.xml:COOKIE:uid=*****;pass=********************
this used to work before I converted to linux, I soo wish it worked now!

thanks everyone.

---

### Post by blastmotor on 2006-08-25
Utorrent has issues with rss feeds that do not directly link to torrents. An example of this would be mininova. You can use [RSS Satellite]("http://rssatellite.sourceforge.net/") to correct the links. Just select a mirror and go to town.

---

