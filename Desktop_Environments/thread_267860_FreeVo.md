---
title: "FreeVo"
date: 2006-09-29
forum: Desktop Environments
---

### Post by WarGasm on 2006-09-29
I have a Tv-Tunner card with Bt878 chipset. I tried to make it work with WinTv but it didn`t. I tried almost all the helps available on the internet. A friend told be about FreeVo and I took it. But this ain`t working either. Here are the errors:

vikernes@vikernes-desktop:~$ freevo

Error: TV_RECORD_DIR not set
Please set TV_RECORD_DIR to the directory, where recordings should be stored
or remove the tv plugin. Autoset variable to /home/vikernes.

Error: VIDEO_SHOW_DATA_DIR not found
ROM_DRIVES: Auto-detected and added "('/media/cdrom0', '/dev/hdc', 'CD-1')"

Error: can't find /tmp/TV.xml
Use xmltv to create this file or when you don't want to use the tv
module at all, add TV_CHANNELS = [] and plugin.remove('tv') to your
local_conf.py. TVguide is deactivated now.

WARNING: /etc/freevo/lircrc not found!
can't locate plugin mixer
start 'freevo plugins -l' to get a list of plugins
failed to load plugin video.mplayer
start 'freevo plugins -l' to get a list of plugins
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/freevo/plugin.py", line 572, in __load_plugin__
    p = eval(object)()
  File "/usr/lib/python2.4/site-packages/freevo/video/plugins/mplayer.py", line 112, in __init__
    _debug_("MPlayer version set to: %s" % config.MPLAYER_VERSION)
AttributeError: 'module' object has no attribute 'MPLAYER_VERSION'


PLEASE HELP ! I`m losing my mind here :(

P.S. I`m a noob so please be kind and explain the step-by-step solution. Thank you !

---

### Post by WarGasm on 2006-09-29
I think I found the source problem.

vikernes@vikernes-desktop:~$ tvtime-scanner
Reading configuration from /etc/tvtime/tvtime.xml
Scanning using TV standard PAL.
videoinput: Cannot open capture device /dev/video0: No such file or directory

how can I fix this ? HELP !!!

---

### Post by reclusivemonkey on 2006-09-29
> **WarGasm said:**
> I think I found the source problem.

vikernes@vikernes-desktop:~$ tvtime-scanner
Reading configuration from /etc/tvtime/tvtime.xml
Scanning using TV standard PAL.
videoinput: Cannot open capture device /dev/video0: No such file or directory

how can I fix this ? HELP !!!

Try 

```

lspci

```

To see if your card has been recognised.

---

### Post by secundar on 2006-12-02
I have a similar problem i think. Here's my card...

```
0000:06:00.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
```

I thought this one was supported yet no /dev/video0 exists.

---

### Post by pauljturner on 2006-12-03
Haven't got it all working myself yet but for the firmware you need to follow this:

[https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy)

---

