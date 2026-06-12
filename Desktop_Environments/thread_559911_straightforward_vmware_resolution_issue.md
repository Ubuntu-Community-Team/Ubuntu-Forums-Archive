---
title: "straightforward vmware resolution issue"
date: 2007-09-25
forum: Desktop Environments
---

### Post by Krusader3z on 2007-09-25
I am only able to go "Full Screen" when my virtual machine resolution is set to 1024x768

Anything over that it it wouldn't go full screen.

I think I see what the problem is. My resolution in Feisty is 1440x900 and I do not see that resolution when I adjust the resolution on my virtual machine(Vista)

Anyone have any suggestions? Also, How do I get those borders i've heard about so I can spin my beryl cube?

Much thanks,
Mike

---

### Post by Mariano Oliveto on 2007-11-15
The same thing happened to me but in WinXP. I hope this helps you but I'm not sure.

I uninstalled VMWare Tools first and then removed the Video Card device from the device manager.

Then I rebooted and reinstalled VMWare Tools using the menu VM -> Intall VMWare Tools as instructed in the other post ([http://ubuntuforums.org/showthread.php?t=300968&highlight=VMWare+resolution](http://ubuntuforums.org/showthread.php?t=300968&highlight=VMWare+resolution)) also edited ~/.vmware/preferences as instructed.

BUT! (this did the trick) what I did to get the same resolution was to only select "Autofit Guest". Somehow this solved it.

EDIT: I also posted this in another thread. Sorry for redundancy! :P (next time I'll just paste a link).

---

