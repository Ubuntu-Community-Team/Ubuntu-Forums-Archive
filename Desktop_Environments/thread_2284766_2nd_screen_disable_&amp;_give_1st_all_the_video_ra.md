---
title: "2nd screen disable &amp; give 1st all the video ram?"
date: 2015-07-01
forum: Desktop Environments
---

### Post by 0-ashley on 2015-07-01
Hello

I have a Ubuntu 15.04 desktop PC with the following configuration:
Core i5 with internal Intel GPU, max 1GB RAM can be allocated, but is disabled in system BIOS.
Nvidia GT630 video card, from my previous computer. 2GB on board video memory. Not a bad card for casual gaming, and this is my main card.

What I want to know is when I enable or disable a 2nd screen, does the video memory get dynamically allocated back to the first screen?

My intention is to use 2x screens for flight sim (both X-Plane & the open source Flightgear support dual monitors) and general use but then use 1x screen for zombie action (Dying Light, Left4dead..) and Team Fortress 2 - first person 3D graphics with as much video ram as possible used on just 1x screen.

In the Ubuntu preferences I can switch on & off the 2nd screen, but I'm not sure whether when No.2 is off all the 2GB video ram is then allocated to No.1? Is there a terminal command I can use to check, or force, this to happen?

I understand the *xrandr *command is a good place to start, not least because I've read you can be specific about where the 2nd screen "appears" relative to the first. I've seen a few script examples to do this. 

If if its a case of popping a script or two in my home folder to switch between gaming & general/flight sim I'm happy.
of course one day I'll buy a better card :-) but for now...

Help very much appreciated,

Thanks

Ashley

---

### Post by 0-ashley on 2015-07-02
I found out what to do, and will mark this one as "solved"

With Nvidia cards, and Nvidia driver, use the *nvidia-smi* command to find out how much video memory your display is using.
In my case, its display 0 as its an extended (not mirrored) desktop.
If I use:
[I]xrandr --output DVI-I-1 --off

[/I]Then:
[I]nvidia-smi

[/I]I get the following:

+------------------------------------------------------+                       
| NVIDIA-SMI 346.35     Driver Version: 346.35         |                       
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GT 630      Off  | 0000:01:00.0     N/A |                  N/A |
| 50%   33C   P12    N/A /  N/A |    184MiB /  2047MiB |     N/A      Default |
+-------------------------------+----------------------+----------------------+

Then if I use:
[I]xrandr --output DVI-I-1 --auto --left-of HDMI-0

[/I]My* nvidia-smi *output looks like:
+------------------------------------------------------+                       
| NVIDIA-SMI 346.35     Driver Version: 346.35         |                       
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GT 630      Off  | 0000:01:00.0     N/A |                  N/A |
| 50%   35C    P0    N/A /  N/A |    266MiB /  2047MiB |     N/A      Default |
+-------------------------------+----------------------+----------------------+

The 2nd display, the larger desktop, does use more video memory (of course) but the important thing is that when switched off the memory usage drops - meaning the display isn't taking up any memory when switched off. I didn't think it would, but wanted to find a way of checking. I think the reason the difference is not precisely half is that I've got this browser + terminal open on just the main screen.

I'm going to use a couple of BASH scripts to switch the 2nd display on and off as needed, using xrandr.

Hope that helps someone,

Best regards,

Ashley

---

