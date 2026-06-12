---
title: "Banshee - How to change back to normal size after full screen"
date: 2011-04-29
forum: Desktop Environments
---

### Post by ndefontenay on 2011-04-29
Hi.

In banshee, I set it to work in fullscreen mode (banshee itself, not the movie or song in the Now Playing panel which is ok).

I never could get back to a normal size. I've looked hard for a button that would let me get back to a window without success.

To reproduce it, just go to view > Fullscreen or press F.

To work around the problem I had to know a few shortcuts, because I didn't know the fullscreen one yet.

I switched into another workspace and whenever I got back to Banshee's workspace I was stuck.

Telling people to press F to get back to a window doesn't seem user friendly.

---

### Post by prometheus83 on 2012-02-21
Hi, 

even though this issue was posted way back I thought I'll share my solution with you. I had the same problem after accidentally maximizing Banshee and my fix was:

(1) Log off and login to your session
(2) Type in *sudo nano /home/$USER/.gconf/apps/banshee-1/player_window/%gconf.xml*
(3) Go to the line   *<entry name="height" mtime="1329815367" type="int" value="1070"/>* and change
the value to something smaller (for example 800) and save
(4) Start Banshee

Hopefully you are now able to readjust the window size. Good luck, 
prometheus83

---

