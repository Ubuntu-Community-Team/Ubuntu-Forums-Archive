---
title: "xubuntu panel problems, failure to respond to mouse clicks"
date: 2017-10-26
forum: Desktop Environments
---

### Post by danbek on 2017-10-26
I've recently installed xubuntu 16.04 on a new computer. I am running into some odd behavior:

1. For every application that I start after the first, no icon appears in the panel at the top of the screen.
2. After I close that first application, its icon continues to display at the top.
3. After running for a while, the menu bars of all my windows stop responding to clicks. So that I can't move the windows, minimize them, bring them to front focus, etc. The body of the window does respond to clicks.
4. Eventually everything stops responding to clicks.

I've run xubuntu 14.04 on other computer for a few years, and never ran into anything like this. It was always very solid.

I don't know how to go about debugging this - are there log files to look for, known GUI bugs? What should I be looking at?

Thank you,

Dan

---

### Post by Autodave on 2017-10-29
What are the specs on this machine? What video card does it have? Have you installed any drivers for the video card? If so, what one and where did you get it from?

---

### Post by danbek on 2017-11-27
This is a brand new Dell Precision T7810, dual-socket Zeon E5-2620 cpus.  32 GB memory. The video card is an nvdia Quadro K620. I've tried three different drivers, all accessed from the "Additional Drivers" tab  under Hardware in the Settings Manager: NVIDIA binary driver 384.90, NVIDIA binary driver 340.102, and the Nouveau display driver. The problems may be subtly different with the different drivers (hard to say for sure, since the behavior is fundamentally flaky), but there are similar problems with all three drivers.

---

### Post by flocculant on 2017-11-28
I'd be inclined to start one of the apps you see the issue with from a terminal, leave the terminal open and alone, run the app and see if anything is shown in the terminal.

Did you see the same problems from the install medium you used - or did you just install it?

You might want to grab the daily dev iso (testing for 18.04), load it on a usb and boot that - see if you get the same problems there > [http://cdimage.ubuntu.com/xubuntu/daily-live/current/](http://cdimage.ubuntu.com/xubuntu/daily-live/current/)

---

### Post by danbek on 2017-11-29
I just installed it, didn't try running from the liveboot - but seeing whether I get the same problem there is a good idea.

It's tricky to track down because it's flaky. Sometimes it goes bad right away, other times it takes 30 or 45 minutes. That has already caused me to think that I had solved the problem when I really hadn't.

---

