---
title: "2D performance becomes unplayable for no apparent reason"
date: 2005-05-04
forum: Gaming &amp; Leisure
---

### Post by Rehevkor on 2005-05-04
Earlier today I installed penguin-command and wesnoth, and both ran great. Nice and smooth, just like they should be. Just now I tried penguin-command and it was so slow it was completely unplayable. Wesnoth was better, but scrolling was incredibly choppy. It was smooth before.

I don't know what the hell went wrong. I'm beginning to reconsider switching to linux completely given how finicky its being. About a week ago nautilus became unable to browse my network shares. Nothing I did had any effect on the problem. Yesterday it just started working again.

I don't even know where to start with this problem. 3D stuff like crack-attack and doomsday run fine, but the 2D games are slow as hell. Frozen Bubble is also effected; the dissolves from one screen to the next are ultra slow. What gives? ](*,)

---

### Post by Rehevkor on 2005-05-05
Does anyone have a clue why its doing this? I also noticed that the "fade" effect when opening the logout menu is very slow. This doesn't happen on the Knoppix live cd; it's smooth and fast there.

---

### Post by DutchLau on 2005-05-05
Open up a terminal and type in " glxgears " and post the FPS you're getting.

Afterwards we can see if you have a hardware or software problem. I'm guessing it's software. We need more, but first show us the results of glxgears  :razz: 

Cheers,

DutchLau

---

### Post by Rehevkor on 2005-05-06
It's averaging about 850 fps. This is on a Radeon Mobility 9000 32mb.
Thanks for helping out btw.

---

### Post by DutchLau on 2005-05-06
Okay, that's not a good sign. You should be getting at least 1000+ fps. I'm averaging out at around 3000FPS with my computer (see sig). Did you install all the ATI drivers? 

[http://ubuntuforums.org/showthread.php?t=24557](http://ubuntuforums.org/showthread.php?t=24557) instructs you to use the package in universe.

[http://ubuntuforums.org/showthread.php?t=22496](http://ubuntuforums.org/showthread.php?t=22496) instructs you to use the most recent drivers from the ATI website.

Install them and see if glxgears works better afterwards,

Good luck!

DutchLau

---

### Post by Rehevkor on 2005-05-06
Ok, I'll give that a shot. I avoided doing this to begin with since it appeared the default drivers were working fine, but I guess I was mistaken :)

Thanks again for your help.

---

### Post by Rehevkor on 2005-05-06
That fixed it! I used the apt-get package version, and everything works great now. Thanks!

---

### Post by DutchLau on 2005-05-06
Alright great!

Post your FPS with glxgears to show off your PC :D

Take care and enjoy Linux,

DutchLau

---

### Post by Rehevkor on 2005-05-06
4662 frames in 5.0 seconds = 932.400 FPS

That's on an Inspiron 8500 notebook with a 2.2ghz P4-M and a Radeon Mobility 9000 32mb. Not exactly a stellar video card, but at least it works properly now :)

---

