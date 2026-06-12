---
title: "Thumbnails in Lubuntu with ffmpegthumbnailer"
date: 2013-06-21
forum: Desktop Environments
---

### Post by Gannin on 2013-06-21
Lubuntu 13.04 uses ffmpegthumbnailer to generate file thumbnails in pcmanfm.  This works well, except for .ogv and .mp3 files.  I'd like to find a way to enable the generation of .ogv and .mp3 file thumbnails.

I know that one solution is to simply install Totem and use its thumbnailer, but I'd like to keep the system lighter than that.  I know another way is to install tumbler and use its gstreamer back-end, however tumbler currently has a bug which causes it to crash when trying to use its gstreamer back-end, which is posted about on Launchpad.

Any other ideas O wise and fair folk?

---

### Post by convertingvegetarians on 2013-06-27
Actually installing Totem does not let PCManFM to start creating ogv thumbnails. It does work for Thunar and Nautilus though.


edit: Totem works for PCManFM also if I restart, sorry!

---

### Post by Gannin on 2013-06-27
Installing Totem also installs its thumbnailer service in /usr/share/thumbnailers.  The current version of PCManFM uses whatever thumbnailers are present in /usr/share/thumbnailers.  In my testing, this is further proven out by installing Totem and appropriate GStreamer libraries and suddenly having .ogv thumbnails appear.

---

