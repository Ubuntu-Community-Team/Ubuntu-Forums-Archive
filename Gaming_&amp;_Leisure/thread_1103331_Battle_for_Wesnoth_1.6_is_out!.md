---
title: "Battle for Wesnoth 1.6 is out!"
date: 2009-03-22
forum: Gaming &amp; Leisure
---

### Post by Perfect Storm on 2009-03-22
[http://wesnoth.org/](http://wesnoth.org/)

Yep, it's here. Have fun.
> March 22, 2009. Once again it's time for that epoch-making event, a Wesnoth stable release. The Battle for Wesnoth team is proud to release version 1.6 of The Battle for Wesnoth, a Free, turn-based strategy game with a fantasy theme and roleplaying elements. The game is available for download now for Windows, Mac OS X and various GNU/Linux distributions.

Release notes; [http://www.wesnoth.org/start/1.6/](http://www.wesnoth.org/start/1.6/)
Changelog: [http://svn.gna.org/viewcvs/*checkout*/wesnoth/tags/1.6/changelog](http://svn.gna.org/viewcvs/*checkout*/wesnoth/tags/1.6/changelog)
Download: [http://downloads.sourceforge.net/wesnoth/wesnoth-1.6a.tar.bz2?download](http://downloads.sourceforge.net/wesnoth/wesnoth-1.6a.tar.bz2?download)

---

### Post by binbash on 2009-03-22
Nice release, thanks for the news

---

### Post by terazen on 2009-03-23
Graphics look nice.  Curious how the gold carryover will play out but the new method seems to make sense. ;)

---

### Post by eragon100 on 2009-03-23
Looks great indeed! The new campaign is fun to play too :)

---

### Post by Vadi on 2009-03-23
Getdeb will have ubuntu .debs up tomorrow.

---

### Post by Gen2ly on 2009-03-24
Good news.  Wesnoth freaking rules!  Only one new campaign but I'll definitely be playing it tonight.

---

### Post by Yashiro on 2009-03-24
> Getdeb will have ubuntu .debs up tomorrow.
Cheers.

---

### Post by BigSilly on 2009-03-24
I have never played Wesnoth. It looks terrifying! I'm not used to strategy games. Is it easy for noobs?

---

### Post by Perfect Storm on 2009-03-24
There's toturial missions and the diffrent campaigns are marked how difficult they are. So even newbies in strategy games can enjoy/learn it.

---

### Post by Vadi on 2009-03-24
And it's up: **[http://www.getdeb.net/app/The+Battle+for+Wesnoth](http://www.getdeb.net/app/The+Battle+for+Wesnoth)**

All campaigns have been grouped into one package, because otherwise there was an absurd amount of them to install. Install order is from left to right (wesnoth-data then wesnoth-music and so on).

---

### Post by Yashiro on 2009-03-24
Brill. :)

Just fyi the darkstar.ist.utl.pt mirror is sending the packages as [text/plain]. The other mirrors are using [application/x-debian-package]

Additionally if you've not installed Wesnoth before you should probably install:

libboost-iostreams1.34.1 (1.34.1-4ubuntu3)
libboost-regex1.34.1 (1.34.1-4ubuntu3)
libsdl-net1.2 (1.2.7-2)
libsdl-ttf2.0-0 (2.0.9-1)

Before you start.


No sound at all here at the moment though. Pff.
*Rectified this. It was Pulseaudio issue. You must have libsdl1.2debian-alsa installed if for some reason you have reconfigured/disabled pulseaudio. Which quite a few Hardy folk will have done. Sadly the audio is very glitchy. Fiddling with the buffersize can improve things, slightly.*

---

### Post by R33D3M33R on 2009-03-25
Great game. I didn't like turn based strategies before, but Wesnoth completely amazed me. Nice graphics, fun campaigns and its FREE! :)

Installation instructions for ubuntu hardy 32bit: 
1. Download all the files to one folder
2. Remove the entire previous installation. Not doing so, can result in broken packages
3. Install libboost-regex1.34.1: 
```
sudo apt-get install libboost-regex1.34.1 
```
4. Install the game:
```
sudo dpkg -i wesnoth*
```

Works fine for me.

---

### Post by kaixi on 2009-03-25
Help me please! I installed the .deb packages from getdeb.net but the menu entry of Battle for Wesnoth doesn't show up in Aplications -> Games

I can see the the Map Editor entry though. What's going on?

---

### Post by R33D3M33R on 2009-03-25
Well, just add it manually. Right click on the menu, select edit, then click new entry and add this:

Name: Battle for Wesnoth
Description: Strategy Game
Comment: A fantasy turn-based strategy game
Command: wesnoth-nolog

Select the proper icon and then save.

---

### Post by Vadi on 2009-03-25
> **kaixi said:**
> Help me please! I installed the .deb packages from getdeb.net but the menu entry of Battle for Wesnoth doesn't show up in Aplications -> Games

I can see the the Map Editor entry though. What's going on?

Are you sure you installed them all? That's the only cause I can think of.

---

### Post by kaixi on 2009-03-25
> **R33D3M33R said:**
> Well, just add it manually. Right click on the menu, select edit, then click new entry and add this:

Name: Battle for Wesnoth
Description: Strategy Game
Comment: A fantasy turn-based strategy game
Command: wesnoth-nolog

Select the proper icon and then save.

Thanks, it works now!

---

### Post by Zenmij on 2009-03-26
> **Vadi said:**
> And it's up: **[http://www.getdeb.net/app/The+Battle+for+Wesnoth](http://www.getdeb.net/app/The+Battle+for+Wesnoth)**

All campaigns have been grouped into one package, because otherwise there was an absurd amount of them to install. Install order is from left to right (wesnoth-data then wesnoth-music and so on).

Thats right to left, no? :confused:

Also, can anyone help me with installing these debs. I get this output:

```
dpkg-split: error reading wesnoth: Is a directory
dpkg: error processing wesnoth (--install):
 subprocess dpkg-split returned error exit status 2
Errors were encountered while processing:
 wesnoth
```

Ok, my mistake, I actually had to go into the directory that contained the debs instead of the dir that contained the containing folder hehe.

---

### Post by Vadi on 2009-03-26
sorry, right to left it is

---

### Post by Gen2ly on 2009-03-27
Anyone having any video trouble?  The only package I've installed is wesnoth and now I'm getting redraw problems.  First when I quit wesnoth the screen doesn't redraw and I have to Alt+Ctl+F1 and then Alt+Ctl+F7 to get it to redraw.  Later when I played Urban Terror I'm getting redraw tracers.  I've rebooted and done this twice and can confirm it.  Sdl is still the same version as before and I already had all the other libraries already on my system so this is directly related to wesnoth.

---

### Post by torgo on 2009-03-28
Weird issue.

I completely uninstalled Wesnoth 1.4 in Synaptic.
 
Then I downloaded and installed the 1.6a deb files from getdeb.net. Now, when I launch the Wesnoth program, the left hand bottom corner says it's still version 1.4. 
What's going on?

---

