---
title: "Resetting screen configuration"
date: 2014-04-20
forum: Desktop Environments
---

### Post by rob50 on 2014-04-20
Hi there,

I'm having a problem with my screen configuration and I wonder if I'm the only one that ran into this:

I have a Dell Precision M6600 notebook with an nVidia Quadro M4000 graphics card. The notebook itself has a 1920x1080 display, at home and at work I also have an additional 27" LCD monitor with the same resolution. This monitor is connected to the notebook with an HDMI cable and it gets detected by Ubuntu when I plug it in.

The OS is a brand new Ubuntu 14.04, I did not install any proprietary drivers. In the display settings, I created a dual screen configuration with the 27" screen left of the integrated notebook display. The 27" screen on the left should be my main monitor. So far everything works as expected.

So here's the problem: as soon as I enter the Ubuntu settings menu, the screens flicker and my 27" TFT monitor gets disabled. All windows and the starter panel are put on my integrated notebook display. When I open the screens configuration in the settings menu, my external monitor is not there. It also does not get detected when I press the button. When I un- and replug the HDMI cable, the TFT monitor gets re-detected and my previously configured dual screen layout gets restored. Sometimes I have to replug even twice. The screen then flickers a bit, then my desired screen layout gets restored.

I noticed that this "layout breakdown" also occurs when I run the standard video player. The second screen disappears and the notebook screen is suddenly the only screen as described above. This also happens when I open a terminal and run x*randr*.

Before Ubuntu I used a Debian 7 which had the very same problem, so I decided to install a fresh system to see if the problem gets solved, but it did not.

I'm really out of ideas, this permanent replugging is really annoying and it surely isn't good for the cable and the notebook. My system is made of standard components, as I would expect for a mobile workstation, so I doubt that my hardware is too exotic or outdated. I should also note that I have absolutely no problem with the very same notebook and monitors when running the Windows 7 on the other HDD, but I of course want and need linux.

Thanks for your help!

---

