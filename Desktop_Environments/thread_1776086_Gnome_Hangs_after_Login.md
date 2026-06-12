---
title: "Gnome Hangs after Login"
date: 2011-06-05
forum: Desktop Environments
---

### Post by Webbo on 2011-06-05
Hi

I have today done a clean install of Ubuntu 10.10. Afer the install I needed to upgrade my video driver (nVidia GeForce MX). I managed to find some instructions to uninstall the existing Nouveau driver and install the nVidia one. This all worked absolutely fine. The first time.

On subsequent logins after the login screen the system just hangs. I get a background screen with shades or purple and a working mouse but nothing else.

I can get to a command prompt (CTRL-ALT-F1) and Ubuntu seems to be working fine - it just seems to be a graphics problem.

I have been going round in circles for several hours now trying to work this out. Please can anyone point me in the right direction?

---

### Post by Webbo on 2011-06-09
I realised that the problem is that all my panels are missing. (I found that I could access the menus using ALT-F1)

I found a [solution to *this* problem]("https://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/151451"):

Open a terminal: ctrl+alt+t
Type: pkill gnome-panel

That gets my desktop working however I seem to need to do this each time I log-in - which is somewhat irritating!

---

