---
title: "Dual monitors freeze up. 12.10 with i915 driver."
date: 2012-12-20
forum: Desktop Environments
---

### Post by zismylaptop on 2012-12-20
This has been reported in launchpad as bug 1079440.

In a nutshell, since 12.10 was installed on my HP mini 110 it cannot use dual monitors for very long before everything freezes up. This computer uses the i915 driver for both the internal screen and the VGA output. The mouse pointer continues to move and if you set it up carefully, you can prove after reboot that the keyboard was also accepting keystrokes.

I can make it happen within a few minutes by setting up activity on both screens and typing on some window.

My gut feel is that this is the driver rather than compiz or some other high-level piece, but I might be wrong. A significant clue that the driver is involved: typing CTL-ALT-F1 causes one of the screens to go blank (the VGA one) but nothing is written to it and CTL-ALT-F7 does not restore the original appearance. This seems to be the only way to make any change to the screens except holding the power button and even that causes no change until both go blank.

If it is the driver, can I replace it fairly easily? Does anybody have any other ideas?

Thanks.

---

### Post by kevinatkins on 2013-03-07
I'm having the same problem and it renders Ubuntu useless for any work - I use dual monitors extensively.. 

I dual-boot Ubuntu and Linux Mint (Cinnamon) on an IBM Thinkpad T60 with Intel graphics. Linux Mint generally behaves fine, and dual monitors no problem. But Ubuntu is another story... I have tried chasing the bug down using various Compiz tutorials, to no avail, so I don't think it's Compiz either, but given that LM works OK, not sure whether it might be something else going on with Unity as opposed to problems with the Intel driver...

Pity though - the penny has dropped for me and I've actually been finding Unity a good, productive work environment; it seems to have improved immeasurably.

---

