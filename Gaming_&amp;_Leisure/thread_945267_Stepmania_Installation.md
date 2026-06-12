---
title: "Stepmania Installation"
date: 2008-10-12
forum: Gaming &amp; Leisure
---

### Post by shynthriir on 2008-10-12
Please help, I miss my stepmania!

I downloaded the binary and threw all the files in ./home/user/.stepmania
Then in terminal I tried running it and it threw this out at me

```
StepMania 3.9
Log starting 2008-10-12 03:09:20
Loading window: gtk
OS: Linux ver 020624
Crash backtrace component: x86 custom backtrace
Crash lookup component: dladdr
Crash demangle component: cxa_demangle
Runtime library: glibc 2.7
Threads library: NPTL 2.7
TLS is available
ALSA: Advanced Linux Sound Architecture Driver Version 1.0.16.
ALSA Driver: 0: HDA ATI SB [SB], device 0: STAC92xx Analog [STAC92xx Analog], 1/1 subdevices avail
Couldn't load driver ALSA: Not enough substreams for hardware mixing, using software mixing
ALSA: Software mixing at 44100hz
Sound driver: ALSA-sw

(stepmania:9940): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed
Video renderers: 'opengl'
Mixing 467.567515 ahead in 511 Mix() calls
Language: english
Current renderer: OpenGL
Theme: default
Error: There was an error while initializing your video card.

   PLEASE DO NOT FILE THIS ERROR AS A BUG!

Video Driver: OpenGL

Initializing OpenGL...
SetVideoMode failed: Couldn't find matching GLX visual

```

I'm still new at all this and all I can make of it is I think it is complaining about my video drivers or something. Running a gateway ML3109, I never manually installed video divers on this laptop, just assumed that Ubuntu did it all for me because it was all working when it booted for the first time.

---

### Post by ramzai on 2008-10-12
Yes, it complains about OpenGL support. You can try to run

glxgears

in the terminal. If it also fails, have a look at [http://help.ubuntu.com/community/Video](http://help.ubuntu.com/community/Video)

---

