---
title: "ISO download speeds influence prospective testers"
date: 2007-01-19
forum: Development CD/DVD Image Testing
---

### Post by UBfusion on 2007-01-19
I think that getting more iso testers depends also on the speed of the iso downloads.

Bittorrent is indeed implemented, but it seems that only 1-2 persons use it (it's rare that I see a second peer when downloading). The torrent usually needs half an hour or more to start from magellanic (is this a bug?) but when it does, speeds are 300-500 kBps - excellent. Http downloads are capped to ~30 kBps max so they are my last resort and take 7-8 hours

Jidgo is a great concept, allowing to download only changes relative to another (already downloaded) iso. The reasons I haven't tried it yet are:

1. I don't know if it is clever enough to realise that I want to update a daily build of e.g. 3 or 7 days ago, which has the same filename as the iso to be updated?

2. I cannot find examples for using to update e.g. 20071118 to 20071119 or Herd2 to 20071119 ?

3. Jidgo is not implemented for the desktop builds.

Ubuntu Herd distros have some mirrors, but there is only one place for the daily builds. Is there room for improvement?

---

### Post by tjotser on 2007-01-19
I am in the netherlands and started downloading the image this morning at +/- 7:00 AM.
It is now 18:30 (just got home) and still going. Thanks for mentioning the HTTP-30kb cap because i was stuck at 10kb/sec and is slowly climbing by " .1 " every 5 minutes.. I did have torrents running today,(I have a 45k/sec max) so that could be it .. I am a registered member at linuxtracker and wouldn't mind uploading torrents everyday,but i also see no other seeds/peers, and Linuxtracker will probably NOT want daily/current builds every day..


:-k
update: i will get it the next hour or so.. to test it (yet again)..

---

### Post by firephoto on 2007-01-19
I've been using rsync to keep the daily kubuntu images updated when I need to.
```

rsync -CvzapP --stats rsync://cdimage.ubuntu.com/cdimage/kubuntu/daily-live/current/feisty-desktop-i386.iso .

```

Don't forget the period on the end.

This is in the wiki somewhere too btw, I just can't find it at the moment.

---

### Post by spd106 on 2007-01-19
It's easy to use jigdo with previous images, you just need to loop mount the old image and tell jigdo-lite to scan it for packages. I usually rename the old image, then I can create the new image in the same directory. Once you have a new image you can delete the old one. Same process every few days or at each new herd.

It's important to make sure that you grab the latest release as the packages don't hang around long. They are replaced quickly by newer ones, making it difficult to complete the image. If this happens you have two options, grab the newer daily .jigdo file or try bittorrent to complete the old image.

When it comes to bittorrent, I think that it could be emphasized more to keep people seeding, even those who got the image via rsync. Perhaps on the dev-announce mailing list or maybe a sticky thread to tell people which torrent is currently the one to get. But we can't expect people to hang around seeding a daily if there is a newer image.

---

### Post by Henrik on 2007-01-20
As firephoto says, rsync makes the download much faster (after having done one).

Instructions can be found here: [https://help.ubuntu.com/community/RsyncCdImage](https://help.ubuntu.com/community/RsyncCdImage)

---

### Post by UBfusion on 2007-01-21
I wrote a prospective mini howto for using rsync on Windows **[here]("http://www.ubuntuforums.org/showthread.php?t=343219")**. Please provide feedback.

---

### Post by Dual Cortex on 2007-01-22
GATech software's library is my favorite server for the downloading of linux ISOs:
[http://www.gtlib.gatech.edu/pub/ubuntu-releases/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/)

No capped speeds.

---

