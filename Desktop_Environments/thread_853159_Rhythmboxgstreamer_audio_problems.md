---
title: "Rhythmbox/gstreamer audio problems"
date: 2008-07-08
forum: Desktop Environments
---

### Post by jkmuller on 2008-07-08
After trying to make my Ubuntu setup work with multiple audio streams, suddenly my Rhythmbox will not play anything. I installed various pulseaudio programs before having these issues, so that might be related. Rhythmbox gives the following error in terminal.

[INDENT](rhythmbox:8436): GStreamer-CRITICAL **: 
Trying to dispose element fakesink, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.


(rhythmbox:8436): Rhythmbox-WARNING **: Unhandled error: Unknown playback error[/INDENT]

Flash audio in firefox works fine. I've also tried reinstalling every gstreamer codec and plugin, as well as rhythmbox, that I could.

---

### Post by glevit on 2008-08-05
i'm having the exact same problem, also after installing a few packages in at attempt to get my cellphone to control rhythmbox over bt.
i also tried reinstalling gstreamer* with no improvement.
please help!

---

### Post by glevit on 2008-08-20
removing ~/.gstreamer-0.10 fixed my problem

---

