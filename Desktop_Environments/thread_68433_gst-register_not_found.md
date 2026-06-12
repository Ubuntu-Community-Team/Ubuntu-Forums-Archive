---
title: "gst-register not found"
date: 2005-09-23
forum: Desktop Environments
---

### Post by vayu on 2005-09-23
I can't play CDs and my volume-control won't show up on the panel when I add it.  When I try to access gnome-volume-control from the terminal (also when I try to play a cd) I get a messagebox that says "Registry is not present or is corrupted, please update it by running gst-register"  When I run gst-register in the terminal (with or without sudo) It returns "command not found"

I tried installing all the gstreamer-0.8 stuff.

---

### Post by sabitha on 2005-09-23
try with gst-register-0.8  :)

---

### Post by vayu on 2005-09-23
gst-register-0.8
starts with "Rebuilding global_registry (/var/lib/gstreamer/0.8/registry.xml) ..."
then it has about a page full of "Added plugin" stuff
Then the last line is: "Illegal Instruction"

When I look at the xml file mentioned there is nothing in it.

---

### Post by sman88 on 2005-10-18
Had any luck with this? I have the same problem and am a total noob so any help would be apreciated.

---

### Post by vayu on 2005-10-19
[QUOTE=sman88]Had any luck with this? I have the same problem and am a total noob so any help would be apreciated.[/QUOTE]

Kind of a hack, but I couldn't get anything else to work, so I copied the registry.xml file from another Ubuntu computer, then installed all the codecs on the Ubuntu Guide. (Which had been installed on the computer with the registry.xml file on it, so I felt that the file would have the same entries in it).

---

### Post by Fousage on 2005-11-02
[QUOTE=vayu]gst-register-0.8
starts with "Rebuilding global_registry (/var/lib/gstreamer/0.8/registry.xml) ..."
then it has about a page full of "Added plugin" stuff
Then the last line is: "Illegal Instruction"
[/QUOTE]

I had a similar problem. I solved it by :

:arrow: sudo gst-register-0.8

and logging out then logging in.

I hope this helps.

Fousage

---

### Post by multisimple on 2008-06-25
from
[http://gstreamer.freedesktop.org/data/doc/gstreamer/head/faq/html/chapter-troubleshooting.htm](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/faq/html/chapter-troubleshooting.htm)
> 
Q: On my system there is no gst-register command.

A: GStreamer version 0.10 does not need this anymore. The registry will be rebuilt automatically. If you suspect the registry is broken, just delete the registry.*.xml files under $HOME/.gstreamer-0.X/ and run

  gst-inspect

to rebuild the registry. 

when i ran this i got gst-inspect
i cant stop terminal to see the begingin
```
..
vmnc:  vmncdec: VMnc video decoder
tta:  ttaparse: TTA file parser
tta:  ttadec: TTA audio decoder
asf:  asfdemux: ASF Demuxer
asf:  rtspwms: WMS RTSP Extension
staticelements:  bin: Generic bin
staticelements:  pipeline: Pipeline object
```
===end

from 
[http://forums.fedoraforum.org/showthread.php?t=60790](http://forums.fedoraforum.org/showthread.php?t=60790)
they ran 

gst-register-0.8

```
Rebuilding global_registry (/var/cache/gstreamer-0.8/registry-i386.xml) ...
Added plugin gstvideofilter with 0 features.
Added plugin typefindfunctions with 66 features.
Added plugin alphacolor with 1 feature.
Added plugin navigationtest with 1 feature.
Added plugin gamma with 1 feature.
Added plugin gstresample with 0 features.
Added plugin sine with 1 feature.
Added plugin dvdlpcmdec with 1 feature.
Added plugin gstmultifilesink with 1 feature.
Added plugin festival with 1 feature.
```

more info on
[http://linux.about.com/library/cmd/blcmdl1_gst-register.htm](http://linux.about.com/library/cmd/blcmdl1_gst-register.htm)



**YES it works!!!**
you have to delete the registry.*.xml files under $HOME/.gstreamer-0.X/ and run

gst-inspect

I removed the whole folder!
you may also need gstreamer0.10-pitfdll or newer look for pitfdll in synaptic
to test it go [http://www.debugmode.com/winmorph/](http://www.debugmode.com/winmorph/) and download winmorph, use wine or anything to extract the video insede and play it with totem, it should not play, after you fixed your problem it should play just fine, the codec is indeo 5, not included in the default totem, if you didnot get this right, but want to still play files in linux, use mplayer.
```

sudo apt-get install mplayer
```

use this or the other
1 for hardy
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install w32codecs
```

2 for any distro
```
wget http://www1.mplayerhq.hu/MPlayer/releases/codecs/essential-20071007.tar.bz2 && tar -xjf essential-*.tar.bz2 && sudo mkdir -p /usr/lib/win32 && sudo cp essential-*/* /usr/lib/win32
```

the only type of folder that i cannot play is 3gp

easy workaround is to convert them to mpeg using Mobile Media Converter, to run just create a shortcut in your gnome menu to Mobile Media Converter

---

