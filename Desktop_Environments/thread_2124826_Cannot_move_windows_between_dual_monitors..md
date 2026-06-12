---
title: "Cannot move windows between dual monitors."
date: 2013-03-12
forum: Desktop Environments
---

### Post by phoyce on 2013-03-12
Hey UF,

I'm a new Linux user, about a month in now.  I'm starting to feel pretty comfortable but this problem has me a bit baffled.  My hardware specs are below and then a brief description of the issue.  Any help would be greatly appreciated.

Laptop:  HP Elitebook 8530p
Monitors:  (x2) HP LP2065

So I'm using Ubuntu 12.04 LTS and life was wonderful when simply working off of the laptop.  However, when I dock it at work where I have a dual monitor setup the top panel is mirrored on both screens and I can't move a window (i.e. Terminator, UberWriter, etc.) across the first monitor to the second monitor.  The window simply hits the side of the monitor and stays.  I can move the mouse across both monitors easily.  I did some research and couldn't find the exact answer I was looking for.  I found some people talking about compiz so I installed that and changed 2 things I thought may help in the settings and my Ubuntu failed to start X so after I fixed that I decided I would revisit compiz in the future. :)

1.  How can I remove the panel from the second monitor as there is no need for it to be on both (screen mirroring is off)?
2.  Please, oh please, tell me how to be able to move an application across one screen to the second.  If Windows can do it I'm undoubtedly sure Linux can do it.

Thanks,
phoyce

---

### Post by lykenstrife on 2013-03-12
I actually have a similar issue, though, I can't switch my audio device to the tv that I use as the second monitor. I would imagine that the two are related somehow, maybe the issue is a driver issue. I am going to toy around here shortly... I might be able to solve both of our issues... I just have one question do you have sticky edges? Also, have you tried the key stroke to move windows to another work space? That might work too

---

### Post by ManamiVixen on 2013-03-12
It sounds like your computer setup the second monitor as a second X session. Meaning you have two independent desktops under one account. In order to get the second monitor working, we need to know your graphics card and whether or not you have proprietary drivers installed.

---

### Post by ManamiVixen on 2013-03-12
[**[COLOR=#000000]lykenstrife[/COLOR]**]("http://ubuntuforums.org/member.php?u=1715432")

Actually your sound has to do with ALSA since the HDMI output has it's own sound chip and most likely uses the same driver as your onboard. To get that working, you have to set the HDMI output as default in ALSA and then switch back to onboard from HDMI when done.

---

