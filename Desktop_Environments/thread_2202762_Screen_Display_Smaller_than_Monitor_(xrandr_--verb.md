---
title: "Screen Display Smaller than Monitor (xrandr --verbose showing all correct)"
date: 2014-01-30
forum: Desktop Environments
---

### Post by daniel107 on 2014-01-30
Okay, quick facts.

New install of Ubuntu 12.04.3 LTS

Just about everything works fine....EXCEPT...the screen Ubuntu is displaying is approx 1" (diagonally) smaller than the actual screen

THE WEIRD PART: The screen is an Asus VS228H-P 22" monitor (which Ubuntu is referring to as an "Ancor Communications Inc 22") with dimensions of 476mm x 268mm and a native resolution of 1920x1080.
     When <<xrandr --verbose>> is run in Terminal, the output shows everything as nominal, it even says it is displaying the correct size. (see attachment). 

What you all are going to ask: I have an AMD Radeon HD 7570 card. I have run the install directions for the proprietary drivers as given here <<http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx/126513#126513>> under the 12.04 option. Tests show fglrx is operating just fine. The screen is connected to the motherboard via an HDMI cable.

After exhaustive searching on the internet (maybe I'm dumb and I missed it) I haven't found anything that will fix this issue (especially the xrandr showing correct information).

Any ideas?

---

