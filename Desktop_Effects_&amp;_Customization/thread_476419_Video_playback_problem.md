---
title: "Video playback problem"
date: 2007-06-17
forum: Desktop Effects &amp; Customization
---

### Post by dr_gonzo on 2007-06-17
Hi all

I have a laptop with the Integrated Intel Media Accelerator 950 GPU. Desktop effects works nice but video playback doesn't work. If I play a video, the sound plays but the video is black. When I don't have desktop effects enabled, the video shows fine. Has anyone here experienced the same issues? Anyone know any workarounds or whatever? I'd appreciate it very much.

Thanks

---

### Post by pingpongboss on 2007-06-17
try totem-xine instead of totem-gstreamer

---

### Post by qamelian on 2007-06-17
Press Alt-F2 to get the "Run Application" box. In the command line of the box, type```
 gstreamer-properties
```.

This open the Multimedia Systems selector. Go to the video tab and change the Default Output Plugin setting to "X Window System (No Xv)". This should fix your problem.

---

### Post by dr_gonzo on 2007-06-18
That worked! Thanks! :)

---

### Post by Benedolt on 2007-06-25
Is there a way I can use the XV extension with desktop-effects enabled?
Does anybody know?

---

### Post by r4idei on 2007-06-25
Try this [http://lists.freedesktop.org/archives/xorg/2007-March/022343.html](http://lists.freedesktop.org/archives/xorg/2007-March/022343.html)
It works flawlessy on my computer, but you're forced to use mplayer

---

### Post by Benedolt on 2007-06-25
Thanks for the tip, r4idei! To use this patch I would have to compile compiz myself though, is that right?

BTW, we are talking about a know bug here: [https://bugs.launchpad.net/xorg-server/+bug/111257](https://bugs.launchpad.net/xorg-server/+bug/111257) Apparently it's being worked on upstream at X.org... (See the upstream link in the launchpad bug report.)

---

### Post by r4idei on 2007-06-26
No no :D It is mplayer related!
The patch for xorg is useless if you have it up to date (for example if you use feisty).

You just have to recompile mplayer :)

(oh and your compiz must have "video plugin".)

---

### Post by Benedolt on 2007-06-27
r4idei, can I ask, what version of compiz you are running? I am running compiz 0.3.6 from the feisty repositories and judging from my gconf keys, it doesn't seem to have the video plugin...

---

