---
title: "[SOLVED]: X failure, cannot reconfigure video card"
date: 2008-09-21
forum: Desktop Environments
---

### Post by pieoncar on 2008-09-21
I was browsing the weekly ad on Best Buy's website (in Flash, fwiw), and all of a sudden my screen went black and I got a warning that I was in low graphics mode.  When I tried to reconfigure, it was telling me that my choices would not work (I am using a Radeon 8500 AIW card with a Compaq TFT8030 monitor - installed Xubuntu a week ago, running the whole time with no problems).

I rebooted and tried displayconfig-gtk again, but I was getting the same "Configuration test failed" message even though I was choosing the ATI driver that was working the whole past week.

To solve the problem, I had to reboot and choose the recovery mode kernel - then I picked the last option, something like "Repair X.org" - then I continued booting normally and everything was back to normal.

It might be weird to post a solved problem, but I couldn't find anything on Google that described the problem I had -- I do find a lot of solutions on these forums, so I thought maybe this would help someone later.

---

### Post by oralalikaroaku on 2008-09-22
Hi thanks for sharing with me as newbie on ubuntu/lin. Im on ubuntu 8.4 dell inspiron700m and having video playback probem. Everytime i click .vob and mpeg. the computer goes to black-screen like about to play in full-screen mode but apparently nothing happen, and i cant go back to the other active application except just "kill" my notebook by pressing power button.

Any help from others? Please....

---

### Post by Brain-free on 2008-09-22
To start, with what kind of player do you open these movies?

Also, try going to Applications -> Add/Remove and search for the package "gstreamer extra plugins". See if after the installation the issue is resolved.

---

