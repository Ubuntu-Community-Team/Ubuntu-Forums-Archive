---
title: "Panels don't display correctly, and max resolution is too low"
date: 2010-05-05
forum: Desktop Environments
---

### Post by willell on 2010-05-05
I just installed Ubuntu 10.04. I have two problems with the display. I'm guessing they're related.

**ONE:**
When ubuntu starts and the desktop comes up, no icons/buttons show up on the top and bottom panels.

And the panels are half-length, even though the "expand" option is checked.

So, every time I reboot, I have to uncheck the expand option in the properties box (this will show all the icons), and then recheck it (if I want the panels to reach across the entire screen space).

Originally, even unchecking/checking "expand" didn't work. I had to change the size from 24 to 25 before I could see any icons. 

Here is what it looks like after starting up:
[IMG]http://img59.imageshack.us/img59/8265/gnomestartupresized.png[/IMG]

**TWO:**
The maximum screen resolution available is 1024 x 768.

Attempting to detect the monitor does nothing. I have a Matrox Millennium G400 graphics card. lspci says the mga driver is loading okay. But I should be able to use a higher resolution than that (at least I did in Windows XP).

**WHAT I TRIED:**
I tried installing the linux driver from Matrox's website, but it threw a "wrong version of X server" error.

I also tried installing the third party driver from tuxx (as explained in [https://help.ubuntu.com/community/BinaryDriverHowto/MatroxParhelia](https://help.ubuntu.com/community/BinaryDriverHowto/MatroxParhelia) ) but it returned the error code 1 (I can get more specific if you need).

I also tried creating an xorg.conf with some card and screen details, but this caused X to fall back to a low-graphics state (the panels were fine then, but the resolution maxed out at 800x600).


Will Ubuntu 10.04 support Matrox G400 Millennium right now and allow resolutions greater than 1024x768? If so, how can I get this to work?

Thanks a lot for your help!

---

