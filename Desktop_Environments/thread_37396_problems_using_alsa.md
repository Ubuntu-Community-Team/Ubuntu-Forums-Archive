---
title: "problems using alsa"
date: 2005-05-27
forum: Desktop Environments
---

### Post by Redsun on 2005-05-27
I can't use alsa, sound runs only if I use oss.

I tried setting the arts demon to use alsa, No sound. Only osssink works. (anyway if I make any application use artssink it crashes. always.)

Seems the alsasink pipeline doesn't respond. If I tell the gstreamer engine to use it, and test it, it tells me:

Failed to construct test pipeline for "ALSA - Advanced Linux Sound Architecture"

Running gst-inspect-0.8 alsasink tells me the pipeline exists.

If I run gst-launch-0.8 alsasink it gives an error, tells me to file a bug and gives this debug info:

gstpad.c(3340): gst_pad_pull: /pipeline0/alsasink0:
pull on pad alsasink0:sink but it was unlinked

I tried alsaplayer, launched it with alsaplayer -o alsa (should use alsa as output), and heard some ogg files... but why can't I use alsa for the system, or with amarok? Is it maybe a gstreamer issue? Am I missing something?

Please help...

---

