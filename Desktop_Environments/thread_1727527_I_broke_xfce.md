---
title: "I broke xfce?"
date: 2011-04-12
forum: Desktop Environments
---

### Post by Zaiken on 2011-04-12
I have been using xubuntu for a couple months now, ran into few problems so far I couldn't fix on my own, but this has me stumped. My last setup (years ago) ran fluxbox so because it was familiar I installed it as a secondary to xfce right off the bat. I download a lot of different stuff because I like to try out all the apps I can find but somewhere I broke something. I can still run fluxbox fine, but nither the Xubuntu nor Xfce sessions will run now. Last thing I remember changing was pulse audio(removed it for an experiment I was trying with jack audio), not sure if it is connected but when I try to login to xfce the screen goes black, flickers a few times then it brings me back to the login screen. I tried failsafe but everytime I do my monitor gives me  a "frequency out of range" error. I tried purging and reinstalling xubuntu desktop and xfce settings but I am thinking its my xorg config. My laptop is a Toshiba satellite M305D-s4830 with ATI Radeon 3100 mobile graphics card and I am running Xubuntu 10.10. Unfortunately I also broke the screen, so right now I am stuck with an external monitor till I get a new one.

---

### Post by Zaiken on 2011-04-12
I fixed it. Somehow my Xfce lost read privileges to .ICEauthority file so it couldn't load. Ubuntu is surprisingly resilient, even after all this trial and error everything still seems to work now that I got it to start.

---

