---
title: "Login Manager crashes when trying to open tiling window manager session"
date: 2021-07-20
forum: Desktop Environments
---

### Post by hugoksp on 2021-07-20
Hi everyone,

I have been using ubuntu for a while but decided to change to lubuntu (21.04) recently for a more lightweight default desktop environment. I have been trying to install different tiling window managers to try it but have been experiencing difficulty (this did not happen with standard ubuntu 20.04). When I choose the session (ex. spectrwm/dwm) and enter my password, the screen immediately freezes, but I can still move my mouse and I can see the top bar printed on the screen on top of the graphical display of the login manager (it does not get cleared). I am pretty sure that the tiling window managers are working as intended as it worked on ubuntu before. How should I troubleshoot this problem?

---

### Post by GhX6GZMB on 2021-07-20
As a Lubuntu user for the last two years, my best advice is: don't.

Stay with the Lubuntu session manager when logging in. 

Written based on painful experiences.

---

### Post by guiverc on 2021-07-20
Are you sure the system is freezing; and it's not that the new WM you're using doesn't actually put up a wallpaper/screen on your monitor/display so you're 'stuck' system is not actually stuck; it's just starting with the `sddm` greeter display as that was the last thing drawn?  (*not all of them will blank your screen*)

Openbox for example doesn't handle the background/screen so you need to have something that handles that. Lubuntu/LXQt uses `pcmanfm-qt` (ie. it's not just a file-manager, but also handles display wallpaper, icons etc) to handle the display; what are you using using on your desired WM as your Lubuntu install won't include any pre-config scripts for "spectrwm/dwm".

FYI:   I'm partial to icewm and light DMs too, but have noticed no issues with them on a Lubuntu base (*I still use x86 laptops with 1GB of RAM so they make sense; though I'm rarely using them except for testing on amd64 hardware as disco or 19.04 release was the last with i386 support*).  *I had a quick play on my last QA-test install; alas it's 20.04 as that's our next release (20.04.3) but I'm not familiar with the WM & focal is too old.*

Later edit:  *I did a QA-test install of impish (what will be 21.10 on release) and added `dwm` and it operates without crashing or problems that I can see (operates identically to focal).  I don't know how to use that WM sorry so I cannot test it fully, but I did not get any crash issues with it on either focal (20.04) or impish (21.10) so I cannot see why you'd have issues on hirsute/21.04 with regards Lubuntu. Both my installs were QA-test installs; ie. clean updated systems with almost no changes/configuration.*

---

