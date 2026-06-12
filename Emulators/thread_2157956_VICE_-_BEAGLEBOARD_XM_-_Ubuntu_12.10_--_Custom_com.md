---
title: "VICE - BEAGLEBOARD XM - Ubuntu 12.10 -- Custom compile"
date: 2013-06-27
forum: Emulators
---

### Post by crvella on 2013-06-27
Hi All

This is my first post here.

I'm trying to get VICE to run in full screen on my tv, through my beagleboard xm.  THere have been a few challenges along the way but for the most part I'm there;  Except for running VICE at full screen.  I have a few questions, which are going to sounds stupid to most of you;

1 - Do I need to install an XServer AND Xclient to be able to run vice?  (I Have to proceed it with startx everytime i want to load it)  I will be running the video out of the beagleboard and not passing it anywhere else to display
2 - Is there some way to ensure that the necesary xclient or xserver (or both) load in the background (I don't want a GUI) so I don't have to proceed the vice executable with 'startx'.  I'm unable to pass paramters when I have to start the vice app with startx
3 - WHat is the lightest weight xserver / xclient that I can install, as the board struggles at the moment with running the thing in full mode
4 - This is the hardest part;  There are a number of options to 'recompile' VICE 2.4 with.  I'm confused as to what to use.  If anyone is familiar with Beagleboard XM and the VICE 2.4 ./configuration - would they be available to assist?  I don't know what options to select for the relevant board, and I get the impression that the more options I select the more it's going to lag.  Optiions like --with-gnome --with-x --sdlui --gtk etc etc.... I don't even know what half these are, let along the light weight ones that will give me what I'm after (Option for full screen and sound)
5 - Once I've compiled, how to I package this to move it to another sdcard and install it on the 'clean' build I have?

Sorry, I know there are a few questions here but I've been stuck on these for a number of days and I've run out of resource.

Thanks in advance

---

