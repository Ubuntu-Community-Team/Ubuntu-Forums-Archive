---
title: "Kaffeine pad error"
date: 2006-05-26
forum: Desktop Environments
---

### Post by walding on 2006-05-26
Hi,

I'm trying to play the BatMan DVD (region 2) on my laptop, but get a pad error in Kaffeine.

gstpad.c(3377): gst_pad_pull: /internal_thread/thread_textbin/textbin/blender:
pull on pad blender:subpicture_sink_0 but it was unlinked

Any ideas?

Walders

---

### Post by an.echte.trilingue on 2006-05-26
Not sure what a pad error is but it looks like a video output error...

Have you tried using different video drivers (under settings --> xine engine parameters --> video)?

xhsm usually works for me.

---

### Post by Jucato on 2006-05-26
you are basically having a GStreamer (the multimedia engine) error. Alternatively, you could try using a different engine like Xine (which is the default for Kaffeine I think).

---

