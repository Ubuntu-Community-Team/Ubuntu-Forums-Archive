---
title: "Extend to multiple display's and mouse key binding"
date: 2012-09-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Xanthius on 2012-09-08
I've been browsing Google, tried multiple things but I can't seem to get my primary monitor to receive a signal. Also, I'm having difficulty setting up a proper keybound.

My system is a Dell XPS L702X, yes with the famous Optimus chip, so yeah no wonder its difficult and as a new user to Linux its annoying as well. But I really dont care about the nvidia chip, just care that my monitors function.

Display Setup:
left- Internal display 1080p
middle - LG 27" 1080p connected on HDMI.
right - 17" Medion screen connected with mini DisplayPort

Currently, the internal (left) and the screen on the right works like a charm as they are both connected on the intel chip.
However, in the very beginning my primary display worked as well however it just said "Ubuntu" in a purple screen. Screen configurations could not find the display, so could not extend it.

First I've tried to install the nvidia driver (bad mistake) purged it when installing bumblebee which did not work. Then I found out there is a Ubuntu specific IronHide continuation of the project so I purged both packages before installing iron hide. That didn't go to well, re-purged everything and installed iron hide again.

This time, getting Ironhide to load properly im getting the error that: "Ironhide hasn't been configured for power management, please run ironhide-configuration."

All fun and all, but "sudo ironhide-configuration" does not enlist such a feature\option except a huge list of configs which just don't work for me (giving me this error, or do not even pass the initial test)


So yeah, now I'm stuck. I believe (in common sense) that the nvidia chip needs to function in order to get a display signal from it.




There is another small thing which still eluded me, key bindings to be more specific mouse related. I use Teamspeak and have it installed working properly. But I want, just as in Windows to have my Logitech G5 mouse button to act as a back button and as a scroll lock toggle at the same time.

A simple GUI interface does not allow for this, so I'm stuck editing files which "should" exist for the X. server for mouse input (according to tutorials) but they dont exist in that directory.

Other tutorials rewrite a specific keybind while I want to add one just as a push to talk key. Scroll lock is pretty much useless, unless this is different in linux ofcourse.

---

### Post by Xanthius on 2012-09-11
I still require help with it.

---

