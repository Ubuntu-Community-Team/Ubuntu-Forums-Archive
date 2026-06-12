---
title: "Dell M1530 No Sound Over HDMI"
date: 2009-04-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by utdps on 2009-04-19
So, I'm tri-booting Ubuntu 9.04 with Vista and Win 7 with the intention that I would just have Ubuntu to play around with.  I haven't used Ubuntu since 7.10 but everything seems easier now.  Well, now I'm using Ubuntu 9.04 as my primary system.  The ONLY thing that is forcing me to boot into the other OSes is to get sound working through HDMI.

I've searched all Wiki's and threads and cannot find similar problems to mine.  Video is working great.  In Windows, you have to change the default sound driver when you want to output sound over HDMI.  I've tried this in Ubuntu but I'm not sure which driver to select.  My choices in Sound playback are:
HDA Intel STAC92xx Analog (ASLA)
HDA Intel STAC92xx Analog (OSS)
ASLA
OSS
Pulse Audio

I've tried each of these and none work over HDMI.  Most work over the laptop speakers.  One weird thing is that I had Digital options on the HDA Intel when I first installed 9.04, but they disappeared somehow.  I reinstalled the drivers from one thread but Digital didn't come back, and sound works on the laptop speakers still but I cannot get the HDMI sound to work.

Hopefully, someone has an easy solution for me.  Thanks

---

### Post by superm1 on 2009-04-19
On the 1530, there is a mixer switch for IEC958.  Flipping that should allow/disallow sound thru HDMI.  Not completely intuitive, bu that's where it's at.

You might need to show the "advanced" mixers in the gnome sound mixer to see it.

---

### Post by utdps on 2009-04-19
Hmm...when I go into volume control, under Device HDA Intel (ASLA Mixer) I have an option for IEC958 Playback Source.  There are several options under playback source but none are outputting sound via HDMI.  The options are Digital Playback, ADAT, Analog Mux 1, 2, and 3.  Any suggestions?  Do I need to restart my system for it to work?

---

### Post by superm1 on 2009-04-19
> **utdps said:**
> Hmm...when I go into volume control, under Device HDA Intel (ASLA Mixer) I have an option for IEC958 Playback Source.  There are several options under playback source but none are outputting sound via HDMI.  The options are Digital Playback, ADAT, Analog Mux 1, 2, and 3.  Any suggestions?  Do I need to restart my system for it to work?
After checking that checkbox, you might still need to set the audio output in your individual application.

For example, in mplayer there is a command line option to send it out hw 0,3 which is generally HDMI

---

