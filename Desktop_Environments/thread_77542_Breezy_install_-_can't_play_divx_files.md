---
title: "Breezy install - can't play divx files"
date: 2005-10-17
forum: Desktop Environments
---

### Post by kmoz on 2005-10-17
Installed Breezy over the weekend and was mostly nothing but impressed.  Until I wanted to get audio/video going.  

Of course, followed the guide as best I could, but came across 2 issues:
w32codecs and libdivx4linux

w32codecs is fixed - i can watch wmv in mplayer without issues.  

When I try an avi divx file though, it plays for a spilt second with sound, then proceeds to lock up mplayer.  totem craps out before that (no surprise there). 

sudo apt-get install libdivx4linux returns:
E: Couldn't find package libdivx4linux

Haven't seen any mention of this on the forums yet...(the divx issue, w32 seems to be a sticking point).  Any help here?  Thanks!

---

### Post by RAOF on 2005-10-17
I recommend installing gstreamer0.8-plugins and gstreamer0.8-plugins-multiverse.  These two metapackages will pull in every gstreamer plugin known to man, and should allow you to play practically anything in totem-gstreamer (or your choice of gstreamer-based player).  It should even pull in gstreamer-pitfdll, which should pick up the win32codecs.

---

### Post by jeffreyvergara.NET on 2005-10-17
im using totem-xine, and installed gstreamer plugins, but I don't remember installing other codecs like win32codec but still plays divx files, I havnt tried .wmv though...

---

### Post by RAOF on 2005-10-17
[QUOTE=jeffreyvergara.NET]im using totem-xine, and installed gstreamer plugins, but I don't remember installing other codecs like win32codec but still plays divx files, I havnt tried .wmv though...[/QUOTE]
Although totem-xine doesn't actually use the gstreamer plugins :)

Whatever works.

---

### Post by kmoz on 2005-10-17
[QUOTE=RAOF]I recommend installing gstreamer0.8-plugins and gstreamer0.8-plugins-multiverse.  [/QUOTE]

So I had already done that.  I reran gst-register-0.8 and now totem can do quicktime, wmv, etc.  still no luck on the divx front though.  I've tried several different avi's and they just won't play.  is there a breezy source for libdivx4linux?  I know in the 5.10 guide is says w32codecs and libdivx4linux are out of the default repos due to licensing.

thanks for the quick replies though.

---

### Post by nasar2k2000 on 2005-10-17
[quote=kmoz]Installed Breezy over the weekend and was mostly nothing but impressed.  Until I wanted to get audio/video going.  

Of course, followed the guide as best I could, but came across 2 issues:
w32codecs and libdivx4linux

w32codecs is fixed - i can watch wmv in mplayer without issues.  

When I try an avi divx file though, it plays for a spilt second with sound, then proceeds to lock up mplayer.  totem craps out before that (no surprise there). 

sudo apt-get install libdivx4linux returns:
E: Couldn't find package libdivx4linux

Haven't seen any mention of this on the forums yet...(the divx issue, w32 seems to be a sticking point).  Any help here?  Thanks![/quote]


i never even got that far...
when o do apt-get for w32codecs it sez that there is package by that name and  etc...
what is going on...i know for a fact that w32codecs did exist i installed it before but now it does not get installled...????

---

### Post by kmoz on 2005-10-19
Okay, fixed issue by reinstalling and redoing gstreamer installs.  Everything is fine now.  whatev, if it works.

Nasar - try this:

wget [ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb)
sudo dpkg -i w32codecs_20050412-0.0_i386.deb

should work fine (it did for me).  According to the 5.10 manual, libdivx4linux and w32codecs were removed from the normal apt sources.

---

### Post by anindya ambuj on 2007-05-02
just use vlc player.. it will be in your synaptic..:) :)

---

### Post by Muad'dib on 2007-05-02
VLC is the way to go.

Doff Totem and the rest, get tge VLC packages and all the plug-ins and you will be set.

---

