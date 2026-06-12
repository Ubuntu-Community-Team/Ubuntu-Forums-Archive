---
title: "Can't remove/move items from Unity Launcher"
date: 2014-09-04
forum: Desktop Environments
---

### Post by krvermeulen on 2014-09-04
I use Ubuntu 14.04 and have 2 problems:
1. I **can't remove items** from the Unity launcher. When I right click on an icon and click on Remove from launcher, nothing happens.
2. I'm **not able to change the order of the icons** in the launcher. I click on an icon and hold my mouse button. Then I move the icon outside of the launcher. A little white line then takes it's place in the launcher. When I move the icon to another location and let the mouse button go, the icon just 'sticks' to my mouse pointer and doesn't set between the other icons in it's new place. Also not when I press a mouse button again. When I press Escape on my keyboard, the icon returns to it's old position.

I have tried the following:
1. Did unity --replace command. Completely froze my system. Rebooted, but didn't solve it.
2. Also tried running dconf reset -f /org/compiz/ and then setsid unity, but no luck either.

Are there any other solutions? Thanks in advance.

Kind regards,
Koen

---

### Post by Mike_Walsh on 2014-09-04
Try sliding the icon up or down THROUGH the other icons, rather than outside the launcher. I had the same problem, when I first started using Trusty and Linux, 3 months ago.

The icon seems to 'lose' its location and settings behaviour once you drag it outside of the launcher. It doesn't work quite the same as some of the 'docks' that are available.

The other problem, I can't help with, unfortunately. Wiser heads than mine may be more able to assist you with that!

Regards,

Mike.

---

### Post by krvermeulen on 2014-09-25
Thanks for replying. It didn't work. Any other suggestions? Switched to XFCE for now.

---

### Post by Sun.Dial on 2014-09-25
Have you tried booting into safe mode (recovery, usually the boot option below the one you'd normally choose in Grub menu), and then rearranging?

---

### Post by krvermeulen on 2014-09-26
Got a DM with a link to this article: [http://askubuntu.com/questions/496368/unlock-from-launcher-option-not-working](http://askubuntu.com/questions/496368/unlock-from-launcher-option-not-working)

All is well now!

---

