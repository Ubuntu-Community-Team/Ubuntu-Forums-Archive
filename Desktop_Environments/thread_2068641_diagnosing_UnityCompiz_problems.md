---
title: "diagnosing Unity/Compiz problems"
date: 2012-10-09
forum: Desktop Environments
---

### Post by ray field on 2012-10-09
for the last month or so, my desktop environment has become highly unstable under 12.01.1. if I leave the computer for over an hour or so, around half the time when xscreensaver has kicked in, I am unable to return to a workable desktop. sometimes all I see is my wallpaper -- not even the Xscreensaver popup will appear -- and everything is frozen. I cannot log out to a terminal, Ctrl-Alt-T to a terminal -- nada. the only thing I can do is cold reboot.

at other times when I am at the keyboard, suddenly Unity/Compiz will simply stop working: often the desktop cube will freeze and everything becomes unresponsive for a length of time from five minutes until twenty minutes or until I simply run out of other things to do and have to cold reboot again. 

on occasion, maybe 25% of the time, I can pull everything together by opening a terminal window and invoking unity --reset.

I have checked all my cards, cleaned out the inside of the computer, checked the temperature. XP, which I admittedly run seldom, gives me no problems at all. last week I thought maybe it was an outdated driver for the Nvidia GeForce 8400 -- I removed the old one and installed the latest one -- but things are not really much more stable. 

it's very frustrating, because I am quite fond of Unity. is there a way to diagnose what is going on? it has the feel of a memory leak. if there is a particular Compiz setting to eliminate -- I'm not really doing that much fancy with Compiz except the Cube and some placed application windows -- I'll try eliminating that. I've been waiting for a fix for the flicker bug (although honestly from my point of view, all of Compiz is a shaky as a house of cards) -- would be happy to give log information to a Launchpad bugtracker, but I don't really know how to trace such a thoroughgoing instability. (Lucid never gave me these problems.)

I should also add that I shell between windowed and fullscreen Dosemu with some frequency, but I can't say this contributes to the instability or not. occasionally fullscreen Dosemu gives me a white/blank screen, but going back to the desktop with Ctrl-Alt F and then back into Dosemu generally fixes that.

---

