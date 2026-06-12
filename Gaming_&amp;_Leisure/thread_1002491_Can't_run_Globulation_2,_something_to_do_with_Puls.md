---
title: "Can't run Globulation 2, something to do with Pulse Audio and Alsa it seems"
date: 2008-12-05
forum: Gaming &amp; Leisure
---

### Post by ubuntu27 on 2008-12-05
Hello Ubunteros! I am having trouble running [Globulation 2]("http://globulation2.org/wiki/Main_Page") (glob2 in the Universe repository).

When I run glob2, it display the windows for  less than 2 seconds and it closes.
When running through the terminal, it shows:

```
ubuntu27@firehome:~$ glob2
Settings::load("preferences.txt") : error, can't open file.
ALSA lib pcm_pulse.c:625:(pulse_prepare) PulseAudio: Unable to create stream: Invalid argument

E: **stream.c: Assertion 's' failed at pulse/stream.c:971, function pa_stream_drain(). Aborting.**
Aborted

```

Can someone help me with this? Thank you in advance.


Here are more info:

Ubuntu 8.10 (Intrepid Ibex)
Linux Kernel: 2.6.27-9
GNOME: 2.24.1
[Glob2]("http://globulation2.org/wiki/Main_Page"): 0.9.3-2

---

### Post by ubuntu27 on 2008-12-05
Let me Bump.

Bump!

---

