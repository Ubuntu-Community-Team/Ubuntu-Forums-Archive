---
title: "Load GPointing Device Settings on startup"
date: 2011-05-19
forum: Desktop Environments
---

### Post by Pille456 on 2011-05-19
Hi,

I've running ubuntu 11.04 on my samsung 900x3A notebook and have a problem using the touchpad:
I've configured my touchpad using "GPointing device settings", but everytime I reboot my system I've to start "GPointing device settings" manually to apply the settings for the current session. Is there a way to do this automatically? 

Secondly I've the following problem:
I cannot use "click and move" with my touchpad. For example, when I try to move a window around: Normally one would click the left button, hold it and move the window via touchpad. But every time I click the left button, any other movement with my touchpad is disabled. Is there a way around this?

Greetings 
Pille

---

### Post by Copper Bezel on 2011-05-19
Weird. You're using Unity or Gnome Classic, then? (Doesn't matter which.)

Are *all* of the settings from gpointing-device-settings being ignored, or just specific ones? We can set some of them manually with Synclient.

So the trackpad motion is ignored while a button is held down? Does clicking and dragging work with tap-to-click, or does it simply not work at all?

---

### Post by Pille456 on 2011-05-19
Hey

I'm using the unity desktop, which works - more or less - fine.
I am not sure, if all options are ignored. Momently I just edited one options: I wanted my mouse to be a bit faster, without going into the gnome settings, because sometimes I use a mouse which is generally faster than the touchpad. 
So I wanted to configure the touchpad speed individually. 

Tapclick + moving works good as one would expect it. The other strange thing is, that the "real" rightlick does not work too and thats the problem I guess. Momently I can rightclick using tap somewhere and hold + leftclick. This is I guess the standard behaviour (and works quite good), but this is not the behaviour I want from my ubuntu. I want to use my physical right click as right click...I hope you know what I mean :smile:
Currently clicking the physical right button is interpreted as a normal left click. 
Maybe ubuntu is here a little bit confused, when I try to move a window, whether I would like to move that window or rightclick somewhere, and so nothing happens.
Also I should say, that the touchpad is a bit "mac-like": The right- and left-button is part of the touchpad and can be used for moving the mouse as well as a physical button

---

### Post by Copper Bezel on 2011-05-19
Oh, *damn* - 900x3a is a *fine* bit o' kit. Pricier than the new Air, but I can see why. 

It's a Synaptics touchpad, right? (You can check in gnome-device-manager.) What you're experiencing isn't at all the normal behavior for touchpad buttons, and I wonder if the drivers on Ubuntu don't fully support the touchpad.

Edit: In the dash, you can search for Startup Applications and add gpointing-device-settings there. Not ideal, though, since it means that you'd have to deal with having the program actually come up; I don't know of any way to have it silently apply its settings.

---

### Post by Pille456 on 2011-05-19
Hio,

Yeha the 900x3A is quite new and I expected some problems, but I didnt thought about the touchpad^^
gnome-device-manager shows this:

Model: SynPS/2 Synaptics TouchPad
Device File: /dev/input/event7

and quite a bit in the properties-tab, which I dont want to copy/paste all. If you need a specific property, let me know which one.

I've never used the gnome-device-manager before (always used lspci and lsmod), but does a '?' at the beginning of a devicename mean, that the driver does not fully support the hardware like it is in e.g. the windows device manager? 
If so, there are quite a lot '?' around... :confused:

---

### Post by Copper Bezel on 2011-05-19
No, the "?" is just the default icon for those entries. I really don't know why (messy program, but sometimes necessary.)

I don't know hardware enough to make any use of the details in the Properties tab. Anyway, it doesn't list the model of the touchpad unit itself, which might have been useful.

I don't know - I don't think there's going to be an easy fix for the buttons, since the gesture suite used under Linux is not provided by Synaptics. You might have to get used to the tap clicking - the two-finger right-click is really quite nice once you get the hang of it. Terribly annoying, though, to have these click regions defined on the trackpad that don't work. Yuck.

For the other part of your question, which properties specifically were you trying to get to set at startup? You can use a script in your startup applications with synclient to do that without loading the Pointing Devices window - it'll just be a little annoying to set up. If you run " synclient -l ", you can get the key names and current values for the settings, then make a list of commands like

synclient VertTwoFingerScroll=1;

for the ones you want to set up and put them in a new executable text file, say, a hidden file called .touchpad-settings.txt in your home folder, that you can add to your Startup Applications. There's a trick to it - Gnome Settings Daemon resets the values, so the synclient script has to run after it does, but this can be managed by a sleep command delay, either in the entry in Startup Applications or at the start of the script itself, like

sleep 30s; ~/.touchpad-settings.txt

For instance, I used this one while I was using XFCE instead of Gnome and having some trouble with certain settings not loading:

```
#!/bin/bash
synclient LTCornerButton=8;
synclient LBCornerButton=9;
synclient RTCornerButton=3;
synclient RBCornerButton=2;
```

There's a *very* weird bug with some of these settings resetting themselves on suspend and wake, but I've only seen it happen with the corner clicks, myself.

---

