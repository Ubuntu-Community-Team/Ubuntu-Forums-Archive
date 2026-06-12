---
title: "Hoary Sound:  GNOME or everything else"
date: 2005-03-13
forum: Desktop Environments
---

### Post by DCuser on 2005-03-13
I'm using an old DELL 500 MHz with built in Sound Blaster compatible sound.  It had no  sound problems with Warty, but now, with the Hoary preview edition, I get sound in GNOME and GStreamer applications, but not others (Macromedia Flash, XMMS, VLC, etc.)

If I issue a "killall esd" command, I can get sound in all the other applications, but GNOME and GStreamer apps are out of luck.

It's not exactly a major annoyance, but is there a workaround?

---

### Post by bobmitch on 2005-03-13
[QUOTE=DCuser]I'm using an old DELL 500 MHz with built in Sound Blaster compatible sound.  It had no  sound problems with Warty, but now, with the Hoary preview edition, I get sound in GNOME and GStreamer applications, but not others (Macromedia Flash, XMMS, VLC, etc.)

If I issue a "killall esd" command, I can get sound in all the other applications, but GNOME and GStreamer apps are out of luck.

It's not exactly a major annoyance, but is there a workaround?[/QUOTE]

The way to get around this is to type:  **killall esd** 
This will k....   

oh....

:)

---

### Post by bored2k on 2005-03-13
For vlc you will need vlc esd plugin. I had to download that to use the only video player i use on Linux. Then go to config and select ESD as audio source.

Same for gxine.

---

