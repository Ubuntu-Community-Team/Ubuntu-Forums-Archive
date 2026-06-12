---
title: "washed out colour for AVI playback in both totem and VLC?"
date: 2006-08-07
forum: Desktop Environments
---

### Post by phrawzty on 2006-08-07
Hello all,

While running the updater this morning, it informed me that Totem would not be automatically upgraded, and that i'd need to use Synaptic to upgrade it instead.  I followed the instructions, and the upgrade via Synaptic appeared to work properly.

Unfortunately, when i attempted to play an AVI file shortly thereafter, Totem informed me that did not have the proper codec - which was strange, because i'd been using it to watch AVIs for quite some time now.

I found and followed the steps outlined in this article:
[https://launchpad.net/distros/ubuntu/+ticket/983](https://launchpad.net/distros/ubuntu/+ticket/983)

Which allowed Totem to play the AVI files again.  Unfortunately, playback has highly washed-out colours (almost black and white).  VLC has the same problem too, oddly enough.

Does anybody have any ideas?   Thanks!

---

### Post by phrawzty on 2006-08-07
Well, perhaps i posted too quickly!  I now have colour again.  My solution is as follows, and as always, YMMV:

Run "gstreamer-properties" from the shell, go to the "video" tab, and select "X Window System (X11/XShm/Xv)" from the "Output" dropdown box.  Test - if you see the coloured bars, then you're in business.

---

### Post by phrawzty on 2006-08-10
Well, after a few days of it working properly, i had to reboot (kernel update).  Now, using "X Window System (X11/XShm/Xv)" produces the washed out colours, and using "X Window System (No Xv)" produces colours properly.

Unfortunately, switching back to "No Xv" produces video with jagged edges, and the playback is not smooth.

Something is clearly amiss here.  Does anybody have any ideas what is going on?

---

### Post by crumja on 2006-08-11
In VLC's advanced options, change the video->output module to OpenGL. Make sure you have direct rendering enabled.

---

### Post by orb9220 on 2006-08-11
I don't know if this applies but to use the video adjustments in xine player they told me to change to XShm. Otherwise I can't adjust brightness contrast,etc...

If that slider is not set at default or set to high will wash out the collors.

wonder if it is related to X Window System (X11/XShm/Xv)
just a thought

---

### Post by proletario on 2007-01-26
Hello,

I'm new to Linux, so I don't have real technical explanations or solutions, however I had the same problem and I tried almost everything on th various forums and sites I found concerning the issue. Finally I think I've solved it using the most basic solution: uninstall and reinstall. Besides that, the only real change I've made to my computer is installing gxvattr, which allows me to change various colour options. So what I did was to uninstall any Xine based player, basically all Media (video) players installed on my system, reebooted and reinstalled MPlayer. Colours worked fine, but DVD playback was a disaster, so I uninstalled it as well, rebooted and reinstalled GXine. That has done the trick! I restarted the program, tried with some avi videos and another DVD and still worked. I've rebooted my machine twice now and still works. It had never really worked for me before since I installed Ubuntu and I had just changed the contrast setting on GXine to get a desent colour, but know it works perfectly without having to make any changes. It might be a dumb solution and there has to be a technical reason behind all this, but it worked. Please try it and let me know if it works for you as well.

Thanks.

---

