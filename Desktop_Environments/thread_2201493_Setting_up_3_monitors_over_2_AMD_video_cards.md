---
title: "Setting up 3 monitors over 2 AMD video cards"
date: 2014-01-24
forum: Desktop Environments
---

### Post by hermdog on 2014-01-24
I have tried a couple of different guilds i have found around the web and none seem to work so im coming here for help

i have 3 monitors across 2 video cards:
03:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Park [Mobility Radeon HD 5430]
05:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Redwood XT [Radeon HD 5670/5690/5730]

the video card in 05:00 is the primary and I have 2 screens running off of that video card.

the card in 03, has 1 monitor connected to it. but i cant seem to get anything loaded.
i have the ati catalyst tool installed, and i can see the first two screens, and a symbol for the second card. but it lists it as unknown device. any action on the settings for the 3rd device(activate screen) require reboot.

when i reboot, no change.

im at a loss here.

---

### Post by QIII on 2014-01-24
Hello!

You need to make sure both cards are initialized and accounted for.

Issue the following in the terminal and reboot:

```
sudo amdconfig --adapter=all --initial
```

let us know if that gets you moving.

Edit:  is this a laptop or a desktop?

---

### Post by hermdog on 2014-01-24
this is a desktop

---

### Post by hermdog on 2014-01-24
i logged out and logged back in(this should restart x i believe)
my catalyst app doesnt seem to be working, looking at that right now.

once this is done if i dont see any changes, ill reboot

---

### Post by hermdog on 2014-01-24
catalyst control center see's all three devices now(thank you for that).

but when i try to set them up i cant seem to set them up as one multi-display desktop

but is says i could do a multi-display(1+2) single desktop(3).
i was thinking i could try this with xinerama.

when i apply the changes, it says i need to restart.
when i do. 3 does not power on, and now 1+2 are clones of each other.. no longer a multi-display...

---

### Post by hermdog on 2014-01-24
im guessing that last reboot took.

currently i have a multi-display desktop(1+2) and a single desktop (3)

the strange thing... there is no theme or windows or anything on this new desktop.

---

### Post by QIII on 2014-01-24
That's because initializing both cards gives you a default setup, which is cloned.  Not at a Linux machine right now (I make the lion's share of my living in Windows) but I'll get back to this tonight.

---

### Post by hermdog on 2014-01-24
awesome! thanx for the help Qlll

---

### Post by jp734 on 2014-01-24
I do have pretty much the same setup like yours with two AMD cards (5450s) and 3 monitors. I created "xorg.conf" file and works flawlessly. Running Lubuntu 13.10

---

### Post by QIII on 2014-01-24
@hermdog --

When you say no windows or theme, do you mean that you are seeing just your wallpaper with no launcher and the like?

Or do you mean that you can open an application, but there are no window decorations, min, max, close buttons?

---

### Post by hermdog on 2014-01-27
I have a white background with a black X for the curser.
any windows I open do not have borders at all.

but only on the"desktop" the third screen is on.

im running ubuntu 12.04

---

### Post by jp734 on 2014-01-29
I had the same issue where my first two monitors connected to the first (main card) works perfectly but the third monitor on the second card is a black screen with and "X" cursor. People have not recommended it at all but the only way for me to fix it is to turn on xinerama.

Xinerama slows 3D acceleration but i don't use 3D so it works for me just fine.

---

### Post by jp734 on 2014-01-29
Also, just want to add, I heard that **xrandr version 1.4** will work on 2 video card setup. So if you can install that on your system, I would recommend that route.

---

