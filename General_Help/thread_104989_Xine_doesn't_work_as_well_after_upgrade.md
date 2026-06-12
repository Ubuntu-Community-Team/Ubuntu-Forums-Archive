---
title: "Xine doesn't work as well after upgrade"
date: 2005-12-17
forum: General Help
---

### Post by jmooney on 2005-12-17
Just got the upgrade notification from synaptic a couple days ago about an new xine library.  Since installing it, some of the .wmv files I could previously play are not working as well.  Some of these weren't working right in mplayer but did work in xine-ui and totem-xine.

Tried re-installing everything, but no effect.  Is this a known problem?

Joe

---

### Post by Kokanee on 2005-12-17
YES! Me too.  I was just about to start a thread about it.

After the update to libxine1c2 the sound on my WMV files stopped working. This happens on Totem-Xine and Xine-ui. Mplayer works fine.  I have tried reinstalling everything related to Xine and Totem and even the win32 codecs!

Is there some way I can downgrade to the previous package?

---

### Post by kaamos on 2005-12-17
Open synaptic, search for the package and choose  "force version" in the menus.

---

### Post by Kokanee on 2005-12-17
Done!  It fixed the problem.  I also selected Lock Version to get the Update popups to shutup.

---

### Post by jmooney on 2005-12-17
downgrading back to previous version worked for me as well.

---

### Post by bonsiware on 2005-12-17
yeah! thank you all!

but downgrading I solved another problem too:
- _pixelated_ video effect on any video

bye

---

### Post by Paul Jones on 2005-12-19
When I upgraded and tried to play an MPEG that had worked fine on the xine that
I got from packages.debian.org, it said it could not find a decoder for MPEG 2/3
audio.  It plays the video ok.

I downgraded per above but I still get this error.  Anyone else see that?

---

### Post by geoybest on 2005-12-20
[QUOTE=jmooney]downgrading back to previous version worked for me as well.[/QUOTE]
I had the same problem. After downgrading from libxine1c2 (1.0.1-1ubuntu10.2) to (1.0.1-1ubuntu10), my favorite online TV channel (in wmv) finally played well as it did a week ago. Before downgrading, totem-xine does not play wmv video smoothly and the sound broke. It took me a lot of time to know where the problem is.

Maybe I should think twice before applying the security update?:confused:

---

### Post by Paul Jones on 2005-12-23
The story ends up for me having to go back to libxine1_1.0.1-1sarge1_i386.deb
and xine-ui_0.99.3-1_i386.deb.  It seems to play everything just fine with audio.

Is this a bug with the way it's built or packaged?

Did anyone file a bug?

---

### Post by hav0x on 2005-12-23
Same problem here.

---

### Post by gamma on 2006-01-31
Same issue here. I'm new to Kubuntu so I've been reinstalling because I thought I broke a config file or something. Glad to know this is the issue, and hope it gets fixed.

---

