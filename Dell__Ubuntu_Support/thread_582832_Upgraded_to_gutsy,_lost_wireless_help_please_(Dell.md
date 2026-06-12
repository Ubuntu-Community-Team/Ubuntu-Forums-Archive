---
title: "Upgraded to gutsy, lost wireless help please (Dell E1505N)"
date: 2007-10-20
forum: Dell  Ubuntu Support
---

### Post by UberIcarus on 2007-10-20
I upgraded to gutsy, the driver is enabled in restricted manager. the card shows up in lspci. But:

fn+f2 does nothing now, its an unknown key combination

ifup/down eth1/wlan0 does nothing.

it does not appear in nm-applet, or network manager.

I have no way to cycle on my radio, or anything.

I thought the wireless pro chipset was supposed to "just work"


help please?

Problem relates to this bug: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/134193](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/134193)

Switching from -386 to -generic fixed it, gutsy was defaulting to -386.
(this is a E1505 that came preinstalled with Ubuntu).

---

### Post by Dellfan on 2007-10-20
What kernal are you running?

 I have a 1505 wth a 3945, upgraded at Tribe 3, through Beta and RC. Currently running latest 2.6.22.14-generic (Sunday Oct 14). Other than one period of weirdness during the beta, wirless has stayed working. Network Manager was broken at one point and would not reconnect after a suspend (would claim  interface was up and I needed to iwconfig/dhclient3 it) but the radio always was working. Has been workig flawlessly for the last week or so, even through multiple suspends / day.

Just tested and Fn-F2 disable/enables the radio, and it reconnects after being re-enabled. Definitely have not done any fiddling with the wireless, other tha enabling the restricted driver.

---

