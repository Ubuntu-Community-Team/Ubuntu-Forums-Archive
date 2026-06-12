---
title: "Streaming CNN *.wmv"
date: 2006-07-18
forum: Desktop Environments
---

### Post by RudolfMDLT on 2006-07-18
Hi,

I just visited CNN's home page and tried to play some of the media on the site. I get a pop up saying that the media is optimized for MS Media Player. Is there anyway around this in Ubuntu? There's no way of just downloading the file, it seems that you have to have MS MP9 installed in order to view CNN's streaming video. I know Totem has a Plugin for *.wmv but on the CNN Site there's an actual script for checking for Media Player. This is a bit odd really... Is there a way to play these files?

---

### Post by jordilin on 2006-07-18
install mozilla-mplayer (the mplayer plugin for firefox) as well as the necessary codecs to play wmv

---

### Post by RudolfMDLT on 2006-07-18
I can play anything on the net. The cnn site just won't allow non windows media player machines... see the attachment. If anybody wants, go to cnn.com and click on the clip on Bush.

---

### Post by reclusivemonkey on 2006-07-18
> **RudolfMDLT said:**
> I can play anything on the net. The cnn site just won't allow non windows media player machines... see the attachment. If anybody wants, go to cnn.com and click on the clip on Bush.

Works fine for me...

---

### Post by llamakc on 2006-07-18
reclusivemonkey, what mplayer* or totem* packages are you using? What was your after-install path for getting CNN's video to work?

---

### Post by reclusivemonkey on 2006-07-18
> **llamakc said:**
> reclusivemonkey, what mplayer* or totem* packages are you using? What was your after-install path for getting CNN's video to work?

I'm using the MPlayer-Plugin for Mozilla; I've found it to be by far the best for multimedia in linux.

```

luke@mother:~$ ls /usr/lib/firefox/plugins/
flashplayer.xpt         mplayerplug-in-qt.so   mplayerplug-in-wmp.xpt
libflashplayer.so       mplayerplug-in-qt.xpt  mplayerplug-in.xpt
libswfdecmozilla.so     mplayerplug-in-rm.so   nphelix.so
libunixprintplugin.so   mplayerplug-in-rm.xpt  nphelix.xpt
mplayerplug-in-gmp.so   mplayerplug-in.so
mplayerplug-in-gmp.xpt  mplayerplug-in-wmp.so

```

I've no idea what you mean by "after-install path" I'm afraid...

---

### Post by llamakc on 2006-07-18
Goofy phrasing on my part. You should me exactly what I needed. I've been using the MediaPlayerConnectivity extension for so long that I forgot what packages to install. Thanks.

---

### Post by H.E. Pennypacker on 2006-07-22
I used to have something else play Internet videos (totem-gstreamer-plugin), and those CNN videos wouldn't play.  Thank God MPlayer fixed that!  I had to switch over to Windows just to watch a single video.  I am definitely complaining to CNN.

---

