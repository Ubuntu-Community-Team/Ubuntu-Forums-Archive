---
title: "DSL problem"
date: 2007-01-13
forum: Debian
---

### Post by Wangsta on 2007-01-13
Hey, I decided to install DSL Linux on one of my REALLY old laptops and it didn't work. Well, it worked, but as soon as it got to the part about my pcmcia card it totally stopped. 

I have a D-Link Air DWL-650 wireless internet card, but DSL just couldn't read it or something.
I later used the boot option "nopcmcia" and it worked. I figured I could configure the internet after I had DSL fully installed. But it turned out to be more difficult. I still can't get the card and DSL to work together.

The problem is: Now that I've got DSL installed, how can I get Linux to notice my wireless card??:confused:

---

### Post by AgenT on 2007-01-13
The 50mb version of DSL uses the 2.4 kernel which may not have the modules necessary for your hardware because the wireless card may be much newer than your laptop and the 2.4 kernel supports somewhat old hardware only.

You have many options if the small 50mb version of DSL does not work for you: You can try the larger DSL version that uses 2.6 kernel or install Debian using the 150mb NetInstall CD and then apt-get whatever you need like Fluxbox (the window manager that DSL uses). DSL, Knoppix and Ubuntu are all based on Debian. Or if you can somehow get Internet access, install the 2.6 kernel if this is possible in the 50mb version of DSL.

---

### Post by RAV TUX on 2007-01-14
*moving to Debian forum*

---

