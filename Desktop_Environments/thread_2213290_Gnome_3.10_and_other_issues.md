---
title: "Gnome 3.10 and other issues"
date: 2014-03-25
forum: Desktop Environments
---

### Post by Da_Panther on 2014-03-25
Hello,

I recenty changed hard drives in my laptop, and thought best to reinstall instead of cloning.

I am running 13.10, but Gnome was not installed with it. I therefore installed Gnome......3.10. To my great sadness, I cannot seem to be able to find a way to install 3.8.4 again. 

I also have an issue with synaptics - on my old hard drive, I had added two lines to the /etc/X11/xorg.conf.d/50-synaptics.conf file to adjust trackpad sensitivity. This file (the xorg.conf.d folder, in fact) doesn't exist anymore. I now have to manually give synclient the command thru a shell every time I log in, because I can't find a way to make the changes permanent.

If anybody can help me with these two situations, I would be grateful!! I have browsed for hours on the internet and cannot find solutions.

Thanks

---

### Post by Frogs Hair on 2014-03-25
Gnome 3.8 is in the ubuntu  repository and if you installed 3.10 from the ppa you and want to remove it there are ppa purge instructions at the link depending on the PPA used. 3.10  will be a available on 14.04 just weeks away . I would avoid desktop PPA s for regular use because they can be problematic. After a few attempts with the Gnome PPA 's I have decided to stick to the repository versions. Distribution upgrades can be difficult remove if they fail.   


[http://www.webupd8.org/2013/09/how-to-install-gnome-310-in-ubuntu-1310.html](http://www.webupd8.org/2013/09/how-to-install-gnome-310-in-ubuntu-1310.html)

---

### Post by grahammechanical on 2014-03-26
We should distinguish between Gnome, the desktop environment (DE), and Gnome Shell, the user interface (UI). Ubuntu is built upon the Gnome DE. So every installation of Ubuntu includes Gnome DE. So, in this sense Gnome is installed. What we do not get by default in a Ubuntu installation is the Gnome UI - Gnome 3 shell. We get Unity 7.

If we want Gnome 3 shell installed by default then we can install Ubuntu Gnome. But the last version of Ubuntu Gnome (13.10) does not include Gnome 3.10 DE because it was released too close to the Ubuntu Gnome 13.10 release date.

[https://wiki.ubuntu.com/SaucySalamander/ReleaseNotes/UbuntuGNOME](https://wiki.ubuntu.com/SaucySalamander/ReleaseNotes/UbuntuGNOME)

Regards.

---

### Post by Da_Panther on 2014-03-26
I was aware of the difference between Gnome Shell and Gnome DE. The question was how to downgrade from Gnome DE 3.10 to 3.8, but I just ended up doing a clean install. Thanks for the help!

---

### Post by Frogs Hair on 2014-03-26
See the link I posted ,  there are instructions  for the Gnome  PPA purge on the bottom of the page.

---

### Post by Da_Panther on 2014-03-26
Thanks, I ended up letting my lack of patience (after making five fresh installs in two days) get the best of me and went for a 6th fresh install. All is good, I'm back on GDE 3.8. 

However, the synaptic settings issue is not resovled. There is no /etc/X11/xorg.conf.d/ folder on my drive. I tried to create it along with the 50-synaptic.conf file, but all that got me was a stall at reboot... three times in a row. I had to use my old hard drive to externally boot and remove it.

Any ideas?

---

### Post by Frogs Hair on 2014-03-26
I think that file is no longer created by default as in earlier versions.

[http://askubuntu.com/questions/4662/where-is-the-x-org-config-file-how-do-i-configure-x-there](http://askubuntu.com/questions/4662/where-is-the-x-org-config-file-how-do-i-configure-x-there)

---

### Post by Da_Panther on 2014-03-28
That's the xorg.conf file, not the xorg.conf.d/ folder. But I found a workaround - I made a startup launcher that basically executes the ```
synclient FingerLow=10 FingerHigh=16
``` command. works great.

---

