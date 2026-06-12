---
title: "Xbox 360 Controller 'Start' Button Mapped To 'Right Trigger' Using Xboxdrv"
date: 2017-02-11
forum: Gaming &amp; Leisure
---

### Post by pc-load-letter on 2017-02-11
I installed the ubuntu-xboxdrv ppa found [here]("http://www.omgubuntu.co.uk/2014/06/ubuntu-xbox-controller-support-xboxdrv-driver") in order to get my wired Xbox 360 Controller For Windows (i.e. the PC version of the Xbox 360 controller) to work with Rocket League for Steam. Everything worked great with the exception of the right thumbstick, whose X and Y axes were reversed. So I edited the thumbstick settings under "Joystick Preferences" in "System Settings." However, when I did that it prevented Steam from loading properly.

Despite entering the correct username and password, Steam would open the "Connecting to Steam..." window and attempt to load, but then kick me back to the login screen. It consistently takes 3-4 attempts before Steam finally "loads." However, when it does the Steam client window doesn't open, the only thing that appears are a series of Steam notifications in the lower right-hand corner of my screen. I can see the steam process running in System Monitor consuming 38 MB of memory, but the client window never opens.

When I revert the "Joystick Preferences" back to their default settings, Steam and Rocket League load without issue. To get around this I've edited the controller settings from within Rocket League to correct the issue with the right thumbstick, but now the 'Start' button is inextricably mapped to the "Right Trigger." And there's no option within Rocket League's controller settings to map the "Start" button.

**TL;DR:** I installed ubuntu-xboxdrv to get my Xbox 360 Controller to work with Rocket League for Steam, but I can't load Steam unless I use xboxdrv's default settings in "Joystick Preferences." I corrected the right thumbstick issue within Rocket League's controller settings, and now the "Start" button is mapped to the "Right Trigger" and I can't edit the button used for "Start" from within Rocket League.

**Edit:** I'm using the new AMD open source drivers on Ubuntu 16.04 and had to use the following terminal command to get Steam to load properly: "LD_PRELOAD='/usr/$LIB/libstdc++.so.6' DISPLAY=:0 steam"

Any help would be greatly appreciated! Thanks.

---

### Post by mattq1 on 2017-07-08
Did you ever end up resolving this? I'm running into the same issue.

---

### Post by wildmanne39 on 2017-07-08
You should start your own thread the person that ask this question has not been logged in since he posted it.

---

