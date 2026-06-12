---
title: "dvd playbackproblem"
date: 2006-01-06
forum: Desktop Environments
---

### Post by fergus.b on 2006-01-06
Hi

I just installed new graphics drivers for my laptop to get direct rendering working. Since then 3d apps are working much better but dvd playback is now all messed up. In totem the edges of the image have green stripes, along the bottom is a bright line and the main image seems to be out of phase. In mplayer the main image is greyish with stripes of color going diagonally across it.

I think there's some setting I need to add to my xorg.conf adaptor section but don't know where to start.

My graphics adaptor is S3 Unichrome Pro IGP, chipset VIA K8N800, and the processor is an AMD 2800+ Sempron.

To get the new drivers working I installed the K7 kernel and used snapshots from [http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/). 

Help appreciated :)

btw, before I was using the vesa driver and had dvd playback although very choppy.

---

### Post by fergus.b on 2006-01-06
Can a mod please correct the title. I left the space out between dvd playback. Thanks!

---

### Post by bulldogzerofive on 2006-01-06
1.  You can change the title yourself by clicking the edit button and then the advanced button

2.  Which engine are you using for totem?

---

### Post by fergus.b on 2006-01-06
Thanks, I changed the title. 

I'm not sure which engine. How do I check?

---

### Post by fergus.b on 2006-01-06
I just discovered that xine plays DVDs fine. So why would the other players not play them properly.

---

### Post by bulldogzerofive on 2006-01-09
You basically have two choices for playing multimedia:  xine or gstreamer.  Everything else (almost) is simply a better graphical front end for those.

Xine is clearly the superior engine as far as i am concerned; i am not sure what the details behind it are, but gstreamer is the default player for ubuntu because it is the official player of the gnome project.  I think there may also be some licensing issues with xine.

To make xine the default engine for totem, use synaptic to install totem-xine.  Note that this will uninstall totem-gstreamer, but don't worry about that.

Once you have that installed, follow the instructions on the "restricted formats" page of the ubuntu wiki and you should be able to watch anything.

---

