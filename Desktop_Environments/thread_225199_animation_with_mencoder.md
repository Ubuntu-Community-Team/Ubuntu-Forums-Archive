---
title: "animation with mencoder"
date: 2006-07-29
forum: Desktop Environments
---

### Post by zortox12 on 2006-07-29
Hi can anyone help me?

Im a student and i have to practise making animations with my digital camera.

i download mencoder with the sudo apt-get install mencoder command and installs fine but when im in the directory with all the photos i type the command that get all the photos into an avi but i get this:
-------
The command i use: mencoder mf:// on:w=800:h=600:fps=25 -ovc divx4 -o output.avi \*.jpg

The error: MEncoder 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Celeron 2/Pentium III Coppermine,Geyserville (Family: 6, Stepping: 10)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
91 audio & 204 video codecs
success: format: 16  data: 0x0 - 0x0
[demux_mf] file type was not set! (try -mf type=xxx)
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

Exiting...

Do i have to install something? Can anyone help me? plz! this is a matter of life and death.:!:

---

### Post by reclusivemonkey on 2006-07-29
Try

```

"mf://*.jpg"

```

at the begining, rather than mf://. If that doesn't work, try the example from the MPlayer man page, which is;

```
mencoder "mf://*.jpg" -mf fps=25 -o output.avi -ovc lavc -lavcopts vcodec=mpeg4
```

---

