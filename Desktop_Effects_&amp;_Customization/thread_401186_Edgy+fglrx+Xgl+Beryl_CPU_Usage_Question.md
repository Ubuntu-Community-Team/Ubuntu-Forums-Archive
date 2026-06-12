---
title: "Edgy+fglrx+Xgl+Beryl CPU Usage Question"
date: 2007-04-04
forum: Desktop Effects &amp; Customization
---

### Post by dowski on 2007-04-04
Hi,

I am running Beryl on my Inspiron E1505 with an ATI x1300 card.  I am using the flgrx driver from ATI.

For the most part I am pleased with how Beryl runs on my system, but there is one issue.  I notice that Xgl uses a fair bit of CPU (up to ~100% on one of two cores) when I scroll in Firefox, rotate the cube, drag windows, etc.  I thought that my GPU should be leveraged for this sort of thing, so I am surprised to see the CPU usage spike.  

Since the laptop is dual-core, it is still responsive when Beryl effects are active, but it just doesn't seem right.  I have done a bit of googling and didn't come up with any answers.  Is anyone else with a similar setup seeing this sort of behavior?  Am I missing something?

Thanks,

dowski

---

### Post by NikoC on 2007-04-04
I do not have a similar setup yet my cpu indeed peeks to 100 % just for one or two seconds when a beryl 'animation' is used...

My setup
1.76 Ghz Pentium-M
Nvidia 6200 go
512 Mb Ram

No solution found yet.

Edit: using Feisty/Beryl with nvidia as rendering platform

---

### Post by glenby on 2007-04-24
getting similar problem - not just fglrx- and beryl.
methinks it's xgl on it's own.
as I am typing this my cpu is at 90%  and I only have one :( 

I am looking for nice settings and other ways to change this.
the old xserver is slower but seems to take less cpu.

---

### Post by sowelie on 2007-05-09
I am having a similar problem on my wife's computer.  Especially noticable in firefox.  Any javascript, flash etc.and scrolling seems to cause high CPU utilization when beryl is enabled.  I am using the open source driver and AIGLX.

System Specs:
AMD Athlon 1800+
512MB DDR PC2100
ATI Radeon X800XT 256MB (AGP4X)

---

### Post by ununoctium on 2007-05-10
same thing here, a solution would be really great

---

### Post by GSF1200S on 2007-05-11
> **ununoctium said:**
> same thing here, a solution would be really great

And I too am in the same boat... As seen below, my laptop is no slouch, and it regularly jumps one core to 90% just using the cube...

---

### Post by xyber411 on 2007-12-01
Okay guys, this really needs to be a bug.  I don't think it has anything to do with the 3d stuff.  Period.  I have reloaded four times now, each time deleting the partitions relating to ubuntu, and it keeps coming back.  So, here's the deal with my issue:
Stock gutsy (7.10) ubuntu cd installation.
upgrade graphics driver to fglrx by using the manual (method 2) instructions found in the [unofficial ati wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide") using the failsafe terminal.  Reboot.
activate 3d effects
BOOM, my cpu starts taking hits left and right.  If I turn on the system monitor, I am able to see that the cpu usage only spikes (and stays at ~100%) when I do something that would usually be offloaded to the gpu (scrolling, cube turning, snow, moving windows).  However, if I click on the processes tab, nothing shows that it is taking ~100% of the cpu...  every process stays under 5%.  Odd to say the least.  I would expect the offending process to at least show itself.
But here's the kicker:  it happens without the 3d stuff too, and even with just the stock gutsy install, just not as pronounced.  When I have 3d effects off, lets say I scroll a window or move a window.  The cpu usage goes up significantly, usually around ~50-75%.  Interesting thing is that in windows it does the same thing, but again, not as pronounced.  This would suggest to me that it is an xorg issue.  I would think that possibly the redraw to the graphics card needs to be more in sync with the refresh rate.  (not sure how to do that, still a bit of a noob).
And yet, isn't aiglx & xgl supposed to offload all this processing to the gpu instead of the cpu?  This is what's puzzling me the most.

Before I install the fglrx drivers (the ubuntu open-source ati driver):
If I do glxgears, the system monitor shows the cpu taking the hit, not the gpu.  If I do glxinfo I get this pertinent information:
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
client glx vendor string: SGI
client glx version string: 1.4
glx version: 1.2
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string 1.3 Mesa 7.0.1

After I install the fglrx drivers:
If I do glxgears, the system monitor shows the cpu taking the hit, not the gpu still.  If I do glxinfo I get this pertinent information:
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
client glx vendor string: SGI
client glx version string: 1.4
glx version: 1.2
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.1.7059 Release

So, That's my $.02

Anyone with any ideas, let us know!!!

---

### Post by jsnelli2 on 2008-02-04
Anybody come up with anything? I'm having the same problem....Nothing has worked as of yet

---

