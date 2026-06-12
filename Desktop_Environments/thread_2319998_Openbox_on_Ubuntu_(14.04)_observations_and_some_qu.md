---
title: "Openbox on Ubuntu (14.04) observations and some questions..."
date: 2016-04-09
forum: Desktop Environments
---

### Post by bra|10n on 2016-04-09
I installed Openbox on top ofn Ubuntu 14.04 LTS and I'm beginning to think Ubuntu would make a great base for a serious O-buntu flavour :lolflag:

For no other reason than because 'I can' I'm running on an Intel stick with 32Gb of space and 2Gb ram with a quad core Atom chip plugged into a TV via HDMI port and this little thing is killing it!

Stable (It's been 9 days so far) and easily offering the 'casual' user the ability to browse the web, read email etc. Even more so with a light-weight D/E... I haven't tried pushing the limits too hard as yet as I'm still feeling my way...

A couple of things I noticed though is the patchy audio. I observed the following; in Openbox sound is only patchy if using Rhythmbox or surprise, VLC. Open audio files (mp3,ogg) in Totem and they play through without a hitch. I haven't got my head around VLC not stepping up yet :confused: Another thing was in Openbox and running Tint2, if Totem player was minimised to the panel then playback was as choppy as the other players. Restore the window to the desktop and the choppy playback vanished. It was a different story in Unity however, where any player I tried worked flawlessly even when minimised to the side-panel. This seems strange behaviour as only the loaded D/E was different.

Enabling a login sound in both D/E resulted in the playback login sound being cut off only to then play-out as apps were opened or menus searched. Strange.

Anyone here using similar hardware, or thoughts on the above sound issues?

---

### Post by v3.xx on 2016-04-09
> I installed Openbox on top ofn Ubuntu 14.04 LTS and I'm beginning to think Ubuntu would make a great base for a serious O-buntu flavour 

I cannot help with your current build, but in the past when I wanted a openbox install to build on I found LXDE to be a nice start.  It gives OB a panel with a few goodies (like a menu) and not much else.  If your 2G of ram ever starts to run out, this could be a good option.

[http://packages.ubuntu.com/trusty/x11/lxde](http://packages.ubuntu.com/trusty/x11/lxde)

):P

---

### Post by ajgreeny on 2016-04-09
You could, similarly to v3.xx's suggestion, simply install Lubuntu and then choose openbox session from the login menu.

Any problems over needed or wanted packages could then be overcome by installing whatever you need, as you need it.

---

### Post by vasa1 on 2016-04-09
> **ajgreeny said:**
> You could ... simply install Lubuntu and then choose openbox session from the login menu.
...
+1.

That's my set-up. I don't see any need to use Openbox on Ubuntu itself.

I don't use VLC or Totem. I use [mpv]("http://ppa.launchpad.net/mc3man/trusty-media/ubuntu") mostly and GNOME MPlayer sometimes. I don't see the issues you've described. And my panel is tint2.

---

