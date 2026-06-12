---
title: "Video thumbnails without Totem"
date: 2009-02-08
forum: General Help
---

### Post by Paqman on 2009-02-08
I never use Totem, so I uninstalled it. However, this means no video thumbnails. Anybody know if I can get the thumbnailer without installing the whole of Totem? Or use another video app (VLC?) as the thumbnailer?

---

### Post by tariqsheikh on 2010-03-28
Install the ffmpegthumbnailer package from synaptic.

---

### Post by Ixtao on 2010-08-22
I did install ffmpegthumbnailer and uninstalled everything totem as I don't use it either. Sadly as soon as totem-common package is removed thumbnailing stops working..

I went so far as to replace all the values with gconf-editor as described in [the FAQ]("http://code.google.com/p/ffmpegthumbnailer/wiki/Faq"). I understand you need to tell nautilus to use another program for thumbnailing, but nautilus doesn't listen.. Okey, so I see ffmpegthumbnailer has a newer version than in the standard repositories so I try to compile but it doesn't detect ffmpeg although it is installed.. Kee, I compile ffmpeg myself for the sake of it but when that didn't make ffmpegthumbnailer 2.0.4 to compile I gave up and reinstalled totem-common

I need a howto..

---

