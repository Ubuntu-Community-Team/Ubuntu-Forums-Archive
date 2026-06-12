---
title: "Sluggish performance"
date: 2005-11-17
forum: Desktop Environments
---

### Post by psyke83 on 2005-11-17
Hello,

I'm having trouble with (K)ubuntu Breezy 5.10 on two of my machines. Both machines are pretty old, but there is definitely a problem related to this distro that's causing slow 2D performance. When dragging windows there is a lag (less noticeable in Kubuntu but very pronounced in GNOME/Ubuntu), and for example, the transparent selection box on the desktop is extremely slow. When I click and highlight an area on the desktop, the system becomes very unresponsive, and the mouse jerks to catch up with the rectangle. I've tested this while running top, and Xorg uses all the CPU while dragging the selection with the mouse. Other operations such as moving a window brings Xorg's CPU to around 50-60%, and merely moving the mouse with no active programs (except top) shows 10-20% cpu usage in Xorg. From idle, Xorg uses about 2-3% cpu. Overall, both machines give the impression of being unresponsive, as most desktop operations are laggy and take up CPU time.

Before I list my hardware, I want to rule out the possibility that my systems are too old to keep up.. that's not the problem here, because I have a solid base for comparison. I burned SUSE 10.0 and Knoppix 4.0.2 and tried both on the same systems. In Knoppix, top shows about 0.2% cpu usage for XFree86 when idle, no more than 2% cpu when moving the mouse, about 8% cpu moving a window, and about the same when using the transparent selection on the desktop. Note that Knoppix uses XFree86, but I installed SUSE and performed the same tests and found similar results to Knoppix, and that uses Xorg. Something's seriously wrong with (K)ubuntu's Xorg, I think.

My hardware is P2 (360mhz) desktop, NVidia TNT2 Pro with 196mb ram and a Dell Inspiron 8000 laptop (700mhz P3, 196mb ram, ATI Mobility M4). Both systems are very responsive under SUSE and Knoppix, but not Ubuntu nor Kubuntu. I've tried many things to eliminate this problem and reinstalled several times, but no luck. I've installed kernel-686, compiled my own kernel, compiled DRI snapshot drivers for my ATI card, installed the NVidia-glx-legacy packages and I even imported SUSE's Xorg config into Ubuntu, none of which helped with 2D performance. Note that 3D performance is fine on both systems when tested with glxgears -printfps, it seems only 2D performance is a problem.

Any help would be appreciated :)
psyke83

---

### Post by mlomker on 2005-11-17
You might want to file a bug report.  They made some major changes to how Xorg is packaged in Breezy.

---

### Post by mcpish on 2005-11-18
I've noticed the same issues with Ubuntu, I'm glad its not just me.  I'm using an Nvidia GeForce 6200 which is a decent card and an AMD Sempron 2500+, I find CPU usage high when moving around windows and the mouse pointer itself isnt a nice smooth motion but is rather choppy.  I've seen other Linux distros with Gnome running on far less capable machines and yet the desktop is smooth and responsive.

---

### Post by psyke83 on 2005-11-24
Just a little update,

I upgraded Kubuntu to the Dapper development release, and I noticed today after upgrading packages (X.org has been upgraded to 7.0RC2), everything is very smooth & fast. Something in Breezy was really slowing down my system, so hopefully Dapper will remain stable enough during development for use, or else Breezy's performance problems will be fixed through its own upgrades (the latter would be ideal...)

psyke83

---

### Post by wobster on 2005-11-25
Same effect here:
Slower KDE than before and especially OpenGL-applications that caused 0% cpu-usage before now cause ~8% load on my P4/2.5GHz. Hope there will be some solution soon

---

### Post by teaker1s on 2005-11-25
have you tried a kernel other than 386i?
[URL="http://ubuntuforums.org/showthread.php?t=85917"]here
[/URL]

my amd xp2200+ works muck better on k7 kernel

---

### Post by wobster on 2005-11-25
Sure. Just reinstalled all possibly related packages. Should I try going for the newest nvidia-drivers maybe?

Update: All that doesn't seem to be an nvidia-driver issue at all. I just wanted to continue some programming-work with emacs. The Motif-rendering is somewhat messed up. At least it's updating very, very slowly. That might also explain why glxgears looks like 20fps here but -printfps delivers >2000fps. 
By the way, Synaptic hangs up my whole system from time to time now: 100% load, no reaction on keyboard inputs.


I just decided to do a full reinstall. I think repairing will take longer here ;)

---

