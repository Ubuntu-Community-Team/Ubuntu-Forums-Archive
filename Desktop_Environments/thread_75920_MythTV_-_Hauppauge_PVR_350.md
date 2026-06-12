---
title: "MythTV - Hauppauge PVR 350"
date: 2005-10-14
forum: Desktop Environments
---

### Post by xeta on 2005-10-14
I've looked at the various setups for the PVR 250 from the forums here. However I'm still having a bit of trouble running MythTV. I can get into MythTV's front end, however when I go to "Watch TV", all I get is a black screen and I need to Cntrl C to get out of the black screen (escape does not work).

```

$mythfrontend
2005-10-14 10:53:24.544 New DB connection, total: 1
Total desktop width=1680, height=1050, numscreens=1
2005-10-14 10:53:24.668 Using screen 0, 1680x1050 at 0,0
2005-10-14 10:53:24.681 mythfrontend version: 0.18.1.20050510-1 www.mythtv.org
2005-10-14 10:53:24.682 Enabled verbose msgs : important general
2005-10-14 10:53:25.018 Switching to square mode (G.A.N.T.)
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for 2005-10-14 10:53:25.845 Joystick disabled.
mythtv, see preceding messages
2005-10-14 10:53:26.058 Registering Internal as a media playback plugin.
2005-10-14 10:53:38.136 New DB connection, total: 2
2005-10-14 10:53:38.347 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2005-10-14 10:53:38.395 Using protocol version 15
2005-10-14 10:53:38.594 Using protocol version 15
2005-10-14 10:53:39.258 Disable DPMS
2005-10-14 10:53:45.344 Opening audio device '/dev/dsp'.
2005-10-14 10:53:45.345 Opening OSS audio device '/dev/dsp'.
2005-10-14 10:53:45.352 Using resampler. From: 0 to 1000
Using the PVR-350 decoder/TV-out
2005-10-14 10:53:45.735 Realtime priority would require SUID as root.
2005-10-14 10:53:45.755 Changing from None to WatchingLiveTV
2005-10-14 10:53:55.292 Waited too long for ringbuffer pause..

```

I also tried to cat /dev/video0 > test.mpg. While this worked one time (I recorded several minutes of a show on the default channel) after a reboot it no longer worked. How would I go about re-installing the ivtv drivers? Plus I'm almost positive there are some weird symlinks in place to make the drivers work the first time. Thanks in advance for any help.

---

### Post by xeta on 2005-10-16
Still no update, I've messed with several items. 

cat /dev/video0 > test.mpg


now outputs with TV video.

---

### Post by GrammatonCleric on 2005-10-17
This may or may not help but have you seen the Ubuntu/MythTV how to at...

[http://www.abarbaccia.com/content/view/13/27/](http://www.abarbaccia.com/content/view/13/27/)

I found it while researching building my own Ubuntu/MythTV system.  I'm considering buying his pre-built system.

[http://www.abarbaccia.com/component/option,com_phpshop/page,shop.browse/category_id,1/option,com_phpshop/Itemid,42/](http://www.abarbaccia.com/component/option,com_phpshop/page,shop.browse/category_id,1/option,com_phpshop/Itemid,42/)

GC

---

### Post by xeta on 2005-10-17
Yea, that how-to helped me get back tv output on video0 but still no go on mythtv. Its probably something simple like that.

---

