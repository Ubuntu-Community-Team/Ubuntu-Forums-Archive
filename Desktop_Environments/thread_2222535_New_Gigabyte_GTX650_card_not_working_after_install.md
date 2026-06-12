---
title: "New Gigabyte GTX650 card not working after install"
date: 2014-05-07
forum: Desktop Environments
---

### Post by jonathan-l-harrison on 2014-05-07
I am running the latest version of Ubuntu 14.04 and fully up to date on my PC

The PC has a video output which works fine, but the machine is slow, so I bought a new Gigabyte Geforce GTX 650 video card.  Installed but when I unplug the screen and plug it in to the card the screen is blank.

I have checked the additional drivers and made sure the the recommended driver is selected.

Displays only shows the one option, but I would expect that unless two screens were simultaneously plugged in, likewise the config manager

I am sure all I have to do is something simple and idiotic, but I do not know what.

---

### Post by buzzingrobot on 2014-05-07
> **jonathan-l-harrison said:**
> 
I have checked the additional drivers and made sure the the recommended driver is selected. 

You rebooted after the new driver was installed, right?

---

### Post by echotech2 on 2014-05-07
FWIW, the Nouveau driver did not work well with my GTX650Ti.  Colours off, sometimes a blank screen, fuzzy fonts etc.  I installed the propietary NVidia driver v331.38 and all is well.

---

### Post by jonathan-l-harrison on 2014-05-07
Sorry for the delay, Yes rebooted several times.  The prob is I can't plug the screen in to the card as I can't see anything!!!

---

### Post by jonathan-l-harrison on 2014-05-07
[HTML]echotech2**Re: New Gigabyte GTX650 card not working after install**
FWIW, the Nouveau driver did not work well with my GTX650Ti. Colours off, sometimes a blank screen, fuzzy fonts etc. I installed the propietary NVidia driver v331.38 and all is well.[/HTML]

Thanks, I'll try it.

---

### Post by buzzingrobot on 2014-05-07
One way to determine of you have a dysfunctional driver versus an unresponsive system when you find yourself looking at a black screen after booting is to see if Ctrl-Alt-F1 (or F2, F3, etc) gets you a black screen with a login prompt.

Also, if you want to use the "Additional Drivers" feature to install a Nvidia driver, you obviously need to boot into a functioning system.  The kernel boot option "nomodeset" is often used in these circumstances. Temporary use of it stands a pretty good chance of allowing a boot into a usable, if degraded, standard GUI.  From there, you can run Additional Drivers, select and install a Nvidia driver.  When you reboot you should be on the new driver.

Here's the wiki howto about using kernel boot parameters like nomodeset: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions).  Note that it outlines a way to get into the Grub menu on an installation ISO.  On an already installed system, holding down the Shift key during the boot process should result in the boot being interrupted by an editable display of the Grub menu.

---

### Post by jonathan-l-harrison on 2014-05-11
Thanks [**[COLOR=#000000]buzzingrobot[/COLOR]**]("http://ubuntuforums.org/member.php?u=1488460")
My issue was not logging in and blank screens, just when i plugged my screen in to the new card it would not work.  Anyway, things ran away with me, as I accidentally pulled the power plug in the card brfore it had shut down and blew the Power supply.  Surprised they don't have built in protection, such as a fuse!!!  Any, had to buy a new one.  Got the card running, but what i find now is the resolution is abot 50% of the internal/built-in video. ????

---

