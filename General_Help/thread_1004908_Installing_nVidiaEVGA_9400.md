---
title: "Installing nVidia/EVGA 9400"
date: 2008-12-07
forum: General Help
---

### Post by 5circles on 2008-12-07
I'm trying to install a new video adapter to replace the onboard video in an HP 6400.

The good news is that the system seemed to automatically recognize the card, and switched the BIOS.  (I don't know if the current setting of PCI is correct -versus PCI-E or anything else), but at least it is displaying.

Unfortunately, when I start up Ubuntu, it comes up in a very low resolution mode - 800x600 or 640x480 I'm guesing.  As a result, the text at the top of the screen is so large that I can't access the System tools, so I can't change the resolution.

Is there a quick way to start the appropriate graphical tool from the command line (my preference)?  Or how can I change the resolution manually?  I think all I really need is to get started and then I can fumble through the rest.

Thanks

---

### Post by 5circles on 2008-12-07
I figured it out, so this is for anyone else having similar problems.

[LIST=1]
[*]Downloaded the Linux driver script from the nVidia site.

[*]Ran rcconf to turn off the gdm service and come up in command line mode.

[*]Ran the nVidia script.  It needed to reconfigure the kernel.

[*]Rebooted. 

[*]Ran rcconf to turn gdm service on

[*]Rebooted.  It worked.
[/LIST]


Mike

---

### Post by sellwowgold2 on 2008-12-07
[size=2][color=#282827][color=#000000][sell wow gold](http://www.virdeal.com),[sell ffxi gil](http://www.virdeal.com),[sell maple story mesos](http://www.virdeal.com),[sell gaia gold](http://www.virdeal.com) [http://www.virdeal.com](http://www.virdeal.com) [/color][/color][/size]

---

