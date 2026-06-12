---
title: "playing video formats in Totem"
date: 2006-07-04
forum: Desktop Environments
---

### Post by katesfb on 2006-07-04
Hi, i realise some one has probably answered this somewhere but i cant get totem to play conventional video formats (says it needs a compressor) so i downloaded the and installed the win32codecs files and the file that is required for gstreamer to enable them, however still cant play anything so i'm not sure that totem can see the formats - what is the correct directory for them to be in? Any help you can give would be much appreciated.

Cheers.

---

### Post by th3james on 2006-07-04
Ur best bet for setting up codecs, among other things is one of these setup scripts:

[BUMPS]("http://ubuntuforums.org/showthread.php?t=181248")
[Easy Ubuntu]("http://easyubuntu.freecontrib.org/")
[Automatix]("http://www.ubuntuforums.org/showthread.php?t=177646")

These will set up all of the media stuff for your system

---

### Post by titus1950 on 2006-07-04
Read this ,it will help...

[https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca](https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca)

---

### Post by joelito on 2006-07-04
My solution

Open synaptic and install all the gstreamer0.10 plugins (I'm assuming you already enabled the universe and multiverse repositories, if not let me know)

If that fails, you can always download either the tote-xine package or mplayer(the one i use, don't forget mplayer-fonts *** well)

---

### Post by katesfb on 2006-07-05
Hi, yes i tried easyubuntu and that seemed to install everything i required to get the video codecs and other required files installed however i still couldnt play any video formats so have dumped gstreamer and installed totem-zine instead and  this seems to work so no need to beat with a large hammer however it does seem to be running very slow in full screen mode but this probably related to the whole system running rather slow - to which i have put another question up on the forum. Anyway thanks for all your help.

Cheers.

---

