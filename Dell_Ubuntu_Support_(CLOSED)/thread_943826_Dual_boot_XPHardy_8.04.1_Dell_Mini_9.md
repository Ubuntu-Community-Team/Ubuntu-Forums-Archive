---
title: "Dual boot XP/Hardy 8.04.1 Dell Mini 9"
date: 2008-10-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wolfganggold on 2008-10-10
Howdy folks!
First post here (that I can remember anyway).

I took delivery of my shiny new Dell Inspiron Mini 9 2 days ago and it's great.  I got it for evaluation purposes at work so went with the Windows XP build.  Our sales people would experience spontaneous skull fractures if I went with Ubuntu :)

However this unit is "mine" so I've felt free to bork it up in any way I see fit.

One thing I've done is to install Hardy 8.04.1 in a dual boot configuration without resorting to an external ROM drive for the installation.  If this ISN'T a novel method please accept my apologies but if it IS, enjoy! :)

The first step is to install Daemon Tools which can be found here:

[http://www.daemon-tools.cc/dtcc/download.php?mode=ViewCategory&catid=5]("http://www.daemon-tools.cc/dtcc/download.php?mode=ViewCategory&catid=5")

If you're not familiar with this application, it makes a virtual ROM drive on your XP system into which you can mount .iso files.  These then behave exactly as they would if they were actual physical CDs or DVDs.  VERY nice!

So, once you install Daemon Tools, download the Ubuntu iso and mount it (right click the Daemon Tools icon in the system tray, go to Virtual CD/DVD-ROM then to Device 0: [X:], then to Mount Image.  Navigate to the ubuntu iso).  It should auto-play just like a physical disk.

Select the install in windows option.  I let it have 6GB of space which is probably really too much but no worries.

Then just let it do its thing.  Once it reboots select the ubuntu option and the install will continue.

I followed the advice in this post to get everything else (really only sound and wireless) working with great success:

[http://ubuntuforums.org/showthread.php?t=910487&page=2]("http://ubuntuforums.org/showthread.php?t=910487&page=2")

So far I'm VERY happy with this unit.  It seems to be very capable and has fairly snappy performance...I'd have to give the edge to Ubuntu in that respect though! :)

---

