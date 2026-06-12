---
title: "Champions of Regnum on Steam - Some problems."
date: 2013-03-06
forum: Gaming &amp; Leisure
---

### Post by futz on 2013-03-06
Installed COR on Steam the other day. The game is not too bad. It has some bugs, but is fairly playable and entertaining. But I have some problems. 

[LIST=1]
[*]I'm forced to play at low res 1024x768 because their video setting software crashes when I try to set it to 1920x1080 (or make any change). I Googled a message from someone saying to edit the cfg file, but when I did that I had to re-install the game. It didn't work. Anyone know how to get this thing working at 1920x1080? I'm running Ubuntu 12.04 64-bit.
[*]When I exit the game it doesn't actually shut off, and Steam refuses to quit until I start System Monitor and kill the game process manually. Annoying. :confused:
[*]When I exit the game it leaves my desktop in 1024x768 mode. Ewww! I have to logoff and back on to get it back to 1920x1080.
[*]I'd go complain at the Regnum forum, but their registration page is broken. Sigh...
[/LIST]

---

### Post by futz on 2013-03-07
For anyone having the 1920x1080 problem, I fixed it. I edited game.cfg again, setting vg_screen_height = 1080 and vg_screen_width = 1920, but this time I set vg_fullscreen_mode = 0 (windowed). Then I restarted the game and it started up properly in 1920x1080 res, except windowed, which doesn't work right. I then went to the Video Settings in-game and checked the Fullscreen box - the game didn't crash and now I have a working 1920x1080 game. It also leaves my desktop in 1920x1080 mode when I shut down the game. Excellent! 

A bonus is that when I shut down just a few minutes ago the game shut down properly. I don't have to kill the process manually anymore. Also excellent!

---

