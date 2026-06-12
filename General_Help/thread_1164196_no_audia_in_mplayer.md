---
title: "no audia in mplayer"
date: 2009-05-19
forum: General Help
---

### Post by ssk.green on 2009-05-19
A strange that i found was no audio in mplayer after installing java

I'm new to ubuntu bu not to linux
when i installed ubuntu for first time i installed sun java 6-13-1 ( by kpakagekit ). During installation it showed some errors. I can't fix it. When rebooted i found an option in boot menu to repair system.
From that i installed java by using** repair broken packages**. Java successfully installed . when i tried to play avi file in mplayer i cant hear sound. No error shown in terminal. 


**Look at the terminal output :**

MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team                                           
CPU: Intel(R) Pentium(R) Dual  CPU  E2180  @ 2.00GHz (Family: 6, Model: 15, Stepping: 13) 
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1                               
Compiled with runtime CPU detection.                                                      
mplayer: could not connect to socket                                                      
mplayer: No such file or directory                                                        
Failed to open LIRC support. You will not be able to use your remote control.             

Playing Tran1df.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [DX50]  664x268  12bpp  23.976 fps  756.1 kbps (92.3 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.10.1 (build 2366/release)
xscreensaver_disable: Could not find XScreenSaver window.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 112.0 kbit/7.29% (ratio: 14000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 664 x 268 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 2.48:1 - prescaling to correct movie aspect.
VO: [xv] 664x268 => 664x268 Planar YV12
A:   7.2 V:   7.2 A-V:  0.000 ct: -0.000 174/174  5%  0%  1.0% 0 0



there is no problem in above output !


i reinstalled ubuntu 9.04
Now i installed all other than java and now i can hear audio in mplayer


Everything worked perfectly and then i tried to install java by synaptic package manager


**The packages installed are :**

gsfonts-x11 (0.21)
odbcinst1debian1 (2.2.11-16build3)
sun-java6-bin (6-13-1)
sun-java6-jre (6-13-1)
sun-java6-plugin (6-13-1)
unixodbc (2.2.11-16build3)


Now after installation i can't hear audio
I'm sure that after this installation only this happened ! 
help me ! :confused:

---

### Post by ellgor on 2009-05-19
Hi,

Go to the mutimedia/video section and follow the sticky on this subject, fixed mine a treat.

Regards, Ellgor.

---

### Post by ssk.green on 2009-05-21
:lolflag:

---

