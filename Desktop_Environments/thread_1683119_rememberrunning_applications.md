---
title: "rememberrunning applications"
date: 2011-02-07
forum: Desktop Environments
---

### Post by alenis on 2011-02-07
I would like that the windows I am working on are reopened automatically at login, so I checked

System -> Preferences -> Startup Applications -> Options Tab -> Check Automatically remember running applications when logging out.


It works but, unfortunately, sometimes windows are reopened in different workspaces.  I have six workspaces and  I usually keep a lot of windows opened, so rearranging them takes long.

Is there a way to ensure that windows are reopened in the same workspace?
Thanks
Alessandro

---

### Post by Krytarik on 2011-02-07
You could generaly use the "Place Windows" plugin of Compiz to stick your apps to specific workspaces, this should also fix your current issue.

"System -> Preferences -> CompizConfig Settings Manager -> Window Management -> Place Windows"

---

### Post by alenis on 2011-02-08
Thanks for the hint. It actually solves the problem. However, having a  NVIDIA card, I have to disable Compiz because of a very annoying bug - when you open more than n windows, with n > 12, more or less, new windows opened are completely black. Disabling Compiz make it possible to open up to 15 windows. But I will probalby change video card soon...

---

### Post by P4man on 2011-02-08
Hmm.. sounds like your videocard is running out of videoram, with 6 workspaces and a dozen apps? Seems kind of quick though. Is this a really old videocard with very low amount of videoram? If its onboard video, you might want to check your bios if you can allocate more system RAM to the videocard.

---

### Post by alenis on 2011-02-08
The video card is not that old...I think. It's a NV 44 (Geforce 6500). I read that there was a bug in the Nvidia proprietary driver causing the black windows that was removed in the latest versions. Actually, I complained about that in the forum but it seems I am the only one suffering from this problem now.

---

### Post by Krytarik on 2011-02-08
How about upgrading to the latest driver package provided by Ubuntu-X-Swat?:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by alenis on 2011-02-09
I'll give it a try, thanks

---

