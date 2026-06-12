---
title: "Watching Movie Trailers with Firefox"
date: 2005-10-20
forum: Desktop Environments
---

### Post by aham925925 on 2005-10-20
Hey everybody,

I enjoy to watch movie trailers on the internet with Firefox....particularly from [http://www.apple.com/trailers](http://www.apple.com/trailers) .

The problem is that every time I start to watch a trailer.....the sound doesn't play.  The video works fine but the sound won't play.

Can anybody help please??

aham925925

---

### Post by mtron on 2005-10-20
well, it works very good with the mplayer-plugin 3.11.

You will need the mplayer package from the reopsitories, the w32codecs from marillat

terminal:
wget [ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb)
sudo dpkg -i dpkg -i w32codecs_20050412-0.0_i386.deb

and grab the source from the latest plugin [http://mplayerplug-in.sourceforge.net/](http://mplayerplug-in.sourceforge.net/) (cause the plugin in the repos is too old). Compiling is very straight and easy when you follow the instructions on the Homepage. Last step is to delete the totem plugin in the /usr/lib/mozilla-firefox/plugins directory, and you can wath the trailers.

Edit: argh. just saw that christooss wrote already a tutorial to set the stuff up.. see: [http://ubuntuforums.org/showthread.php?t=75817](http://ubuntuforums.org/showthread.php?t=75817)

---

### Post by manis on 2005-10-20
Hi,
I use gxine ( as plugin for firefox) to see the trailer at apple as you suggested.
The sound and picture is very good. 
I also use mplayer when i surfing using mozilla browser. 
This is the best thing in linux - the choice is your.
:p

---

### Post by aham925925 on 2005-10-20
How do you install gxine??

---

### Post by dspp on 2005-10-20
[QUOTE=aham925925]How do you install gxine??[/QUOTE]

Gxine should be available via, among other places, Synaptic.

---

### Post by emperor on 2005-10-23
[quote=aham925925]Hey everybody,

I enjoy to watch movie trailers on the internet with Firefox....particularly from [http://www.apple.com/trailers]("http://www.apple.com/trailers") .

The problem is that every time I start to watch a trailer.....the sound doesn't play. The video works fine but the sound won't play.

Can anybody help please??

aham925925[/quote] 
I found that I needed to install "alsa-oss".
Also  make sure that "Preferences/Multimedia Systems Selector" is set to "OSS" as the "Input". Output should be "ESD".

The "mplayerplugin" works for both WMP and QT, video and sound.
Both mplayer and the plugin are in "multiverse" repo; no need to use the debian "marilet" repo.

Check Firefox plugins via "about: plugins" and remove "totem" and/or "gxine" from your home ".firefox" and ".mozilla" plugin directories.

After  days of struggle, the above solution is the only one that works in all cases.

For full screen mode with the plugin, use the configure menu option when playing trailers to set "xv" for video. The plugin will NOT use the video mode selected in mplayer. The ATI video driver turns "xv" off by default, and enables GL instead, so you may need to edit "xorg.conf" as well

---

