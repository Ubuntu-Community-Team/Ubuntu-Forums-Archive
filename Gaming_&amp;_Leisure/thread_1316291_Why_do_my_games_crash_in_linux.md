---
title: "Why do my games crash in linux?"
date: 2009-11-05
forum: Gaming &amp; Leisure
---

### Post by Jaraxle on 2009-11-05
I find linux to be rock solid, except when it comes to games. Maybe it's something I'm doing wrong, but it seems like all my games crash in the same way. While I'm playing, the game will switch from full screen to a small screen in the upper left-hand corner. This happens with Quake, Quake Wars, Quake III, and Urban Terror.

The game won't take any input using either the mouse or keyboard, and I'm also not able to use Alt + Tab, Alt + F4, or Ctrl + Alt + Del to switch back to fullscreen or exit. The worst part is that I don't have control of the mouse or keyboard in linux. I can't bring up System Monitor or use Shut Down. All I can do is power off.

In the mean time, the game is still running. The system isn't completely locked up, I just have no control. All that I've been able to do is switch to a different virtual terminal and run sudo shutdown -r now. I'm trying to find a way to use ps to kill the process on the default terminal (tty7). Does anybody know how to do that? I've tried reading through the help but can't figure it out. I've managed to have ps list all the running processes on tty7 but for some reason the game wasn't listed. I wouldn't know how to kill a process running on a different terminal anyway. I guess I'll have to study up on that.

Also, does anyone know why this is happening? I don't think it's anything I'm doing, it seems to be random. At times, I thought it was me hitting something like Ctrl + Z or Ctrl + X and that was a command to minimise the game but then I can't reproduce the error again. It seems like everything is fine and then the game just goes into a small screen and won't take any input. This is especially bad when playing multiplayer online. 

I just want to enjoy some games on Ubuntu! Oh, and I'm running X.org 11 on Ubuntu 9.04 Jaunty with GeForce 7050/NVIDIA nForce 610i proprietary drivers. Thanks.

---

### Post by ad_267 on 2009-11-05
It's a known bug that has been around for years and is very annoying. You can either disable the screensaver or disable desktop effects to fix this.

---

### Post by Jaraxle on 2009-11-05
Really? I would have never thought of that. So, if I disable my screen saver and desktop effects, that will solve the problem? I'll gladly disable them right now! Thanks.

---

### Post by ad_267 on 2009-11-05
Not both, just one or the other. I have the desktop effects disabled. Here's the main bug report: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/155263](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/155263)

It looks like this has been fixed in 9.10.

---

### Post by canningtony16 on 2009-11-21
Since you are facing problem while playing games only,so for sure this isn't a problem with OS at all.If disabling screen saver or desktop effects doesn't help,you can try to upgrade your Video card.Since you are already using NVIDEA,you can try ATI Radeon&#8482; HD 5970 which is really fast.

---

### Post by joeelmex on 2009-11-21
I installed a program called caffeine and it disables the screen savers whenever you plat games.  Try it.

---

