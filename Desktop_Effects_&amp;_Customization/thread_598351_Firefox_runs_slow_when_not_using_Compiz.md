---
title: "Firefox runs slow when not using Compiz"
date: 2007-10-31
forum: Desktop Effects &amp; Customization
---

### Post by gcrussell1 on 2007-10-31
A couple days ago I posted a relatively unnoticed question about Battle for Wesnoth running extremely slowly, which I later edited as solved when I turned off Compiz effects (via Appearance --> Visual Effects --> None). However, since this occurred, I've been running into the opposite problem, which is that Firefox crawls when Compiz is *disabled*, but not when it's enabled. The slowdown is manifested in long load times, slow typing (regardless of how fast I type, it shows up, both in forms and in the address and search bars, at about 1 keystroke a second), and in slow Flash performance, where Flash videos and games run at full speed, but the image moves in one-second jerks at twice the normal speed with one-second visual (but not audio) pauses in between. The easy solution is keep Compiz effects running when using Firefox, but it seems that something needs to be fixed.

I'm running Gutsy with a Mobility Radeon 9600 with 128 MB dedicated memory (running the restricted drivers and xgl_server or something, as per a post elsewhere on the forums), as well as otherwise ample processing power and memory.

Any ideas?

---

### Post by vegor on 2007-10-31
Howzit!

I've got exactly the same problem, with exactly the same hardware.
I have a Fujitsu Siemens Amilo D 1840 Notebook with a Mobility Radeon 9600 128MB AGP Graphics Card. I am running Gutsy with fglrx (The restricted ATI driver). With compiz and effects enabled I get jerky 3D graphics, and with it disabled I get a slow firefox. I Hope somebody is gonna fix this.

---

### Post by screaminj3sus on 2007-10-31
that's really weird, exactly the opposite here, firefox runs like COMPLETE **** with compiz enabled. (nvidia 7600GS)

---

### Post by Nacchio on 2007-11-27
I have the same problem with ati 9600 mobile and with nvidia 6200 with two different machine. :confused:

---

### Post by kinkdxm on 2008-02-01
ati card.
when desktop effects are NOT enabled firefox is very very slow.

---

### Post by vkingpele on 2008-03-09
I've been getting the same problem. I shut off Compiz effects and typing in Firefox is slow as hell. Some are saying it's a problem with restricted drivers. And if you shut off the drivers and Compiz, then your typing speed will go back to normal. 

In my case I'm trying to get rid of  the Compiz effects, but keep the restricted drivers enabled. So far my only solution has been to disable Compiz and when I load the computer I have to load into fail safe mode. Then everything goes back to normal. Typing, game playing, etc.

My thinking is that it has something to do with Xgl still being on even though Compiz is turned off and that that interferes with the restricted drivers (RD). Together they seem to play nice. 

RD pass info to Xgl then Xgl passes it back to RD. It seems as though RD is still passing info to Xgl, but with Compiz off Xgl just hangs for a second before returning control to RD. That would explain the slow typing. Anyway, I have no solution besides running in Failsafe mode when Compiz is turned off.

Edit: ATI Graphics card, Restricted Drivers, No Compiz-fusion enabled, but Xgl still running.

---

