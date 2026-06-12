---
title: "Quake2 on Hoary"
date: 2005-10-11
forum: Gaming &amp; Leisure
---

### Post by agger on 2005-10-11
So, I got quake2 from universe, and try to start it from the command line.

This is what I get:

```
 
%~> quake2
QuakeIIForge 0.3
using /home/agger/.quake2/baseq2/ for writing
couldn't exec default.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
loading oss sound output driver, ok
oss: buffer size is 16384, 8192 samples
sound sampling rate: 11025
------------------------------------
------- Loading ref_softx.so -------
LoadLibrary("ref_softx.so") failed: No such file or directory
Refresh failed
Trying mode 0
------- Loading ref_softx.so -------
LoadLibrary("ref_softx.so") failed: No such file or directory
SNDDMA_Shutdown
recursive shutdown
Error: Couldn't fall back to software refresh!

```
What is going wrong - am I missing some package Synaptic doesn't know about?

T a lot IA ... .-)

---

### Post by jadugarr on 2005-10-11
It looks like it can't find libraries for software video from your output.  I have Q2, but I installed it using the loki installer as i didn't know it was in universe.  Check out this thread, [http://www.ubuntuforums.org/showthread.php?t=22920]("http://www.ubuntuforums.org/showthread.php?t=22920") .  It seems others have had similar problems with sound and video, and have a few solutions. Good Luck.

---

### Post by agger on 2005-10-12
[QUOTE=jadugarr]It looks like it can't find libraries for software video from your output.  I have Q2, but I installed it using the loki installer as i didn't know it was in universe.  Check out this thread, [http://www.ubuntuforums.org/showthread.php?t=22920]("http://www.ubuntuforums.org/showthread.php?t=22920") .  It seems others have had similar problems with sound and video, and have a few solutions. Good Luck.[/QUOTE]

OK, I got so far by installing all the files mentioned in that tarball, but now quake2 complains it can't find files under "/pics" - maps and stuff.

But I *did* install "quake2-data"?
Well, I guess I'll probably have to try the loki installer instead.

---

### Post by jadugarr on 2005-10-12
[QUOTE=agger]OK, I got so far by installing all the files mentioned in that tarball, but now quake2 complains it can't find files under "/pics" - maps and stuff. But I *did* install "quake2-data"? That's odd. Maybe not all of the files were installed.  Well, I guess I'll probably have to try the loki installer instead.[/QUOTE] That's odd. Maybe not all of the files were installed. The loki installer was easy to use, just pop in the cd and choose a directory to install to.

---

### Post by agger on 2005-10-13
Naw - I think I'll start by upgrading to breezy and see if quake2 works from the breezy repositories :-)

---

