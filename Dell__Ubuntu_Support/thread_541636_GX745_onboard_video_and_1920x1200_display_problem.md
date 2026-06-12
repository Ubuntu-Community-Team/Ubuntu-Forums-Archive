---
title: "GX745 onboard video and 1920x1200 display problem"
date: 2007-09-03
forum: Dell  Ubuntu Support
---

### Post by Nick Payne on 2007-09-03
I have an Optiplex GX745 using the onboard Intel 865 video to a Dell 2407 monitor which has a native resolution of 1920x1200. The machine is dual boot Windows XP and Ubuntu 7.04. On Windows I can get the display to run 1920x1200 without any problem, but although I selected 1920x1200 as one of the resolutions for X during the Ubuntu install, the display defaults to the next lower selected resolution of 1280x1024 when X starts. I had a look at xorg.conf and 1920x1200 is the primary resolution specified for each colour depth. How can I get the video to drive the monitor at 1920x1200?

Nick

---

### Post by Afishionado on 2007-09-03
Let's try the simple option first. :)

System -> Preferences -> Screen Resolution

and see if the resolution you want is available there.

If not, it's probably just a matter of tracking down and setting up the right drivers.

---

### Post by Nick Payne on 2007-09-03
Thanks, but I'd already checked that - the 1920x1200 resulution is present in xorg.conf but doesn't appear as a choice under Screen Resolution. I also had a play around with 915resolution, and although I could get 1920x1200 to appear as a choice in the video BIOS, it still wouldn't appear under Screen Resolution.

In the end I reinstalled with the latest tribe 5 of 7.10 and it automatically gives me the correct resolution on the monitor.

---

