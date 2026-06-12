---
title: "Automatic updates hosed my display settings"
date: 2008-01-21
forum: Desktop Environments
---

### Post by MountainX on 2008-01-21
I did a clean install of Ubuntu 7.10 AMD 64 today on my desktop. The Ubuntu install was uneventful. After the install, before anything else, I carefully installed Envy and let it get the drivers for my nVidia card. I did things in this order because of the prior problems I have been having. What I did is described here:

[http://forum.compiz-fusion.org/showthread.php?t=6687](http://forum.compiz-fusion.org/showthread.php?t=6687)

I can't use Compiz-Fusion, but otherwise my dual monitors were set up as I wanted them. Next I installed the 168 updates available. After doing that I lost all my desktop and monitor settings.

I've only been using Linux for a couple days, but already I almost have xorg.conf memorized (which is not a good thing!) I edited xorg.conf and put it just how I wanted it, I checked the restricted drivers tool and my driver was enabled. I restarted X, but things still weren't right -- not even close, including no twinview. 

Nnvidia-settings wouldn't open and it suggested i run nvidia-xconfig as root. I did that, but it didn't solve the issue.

What should I have done first? What should I do now? Thanks.

BTW, installing and setting up Ubuntu has been hard! I'm committed to getting it working, but it hasn't been easy. However, I have seen enough good stuff to convince me that I don't want to go back to MS Windows. But I can see why a lot of people sticking a toe in the water decide not to take the plunge. It's too bad...

---

### Post by damoek on 2008-01-21
hey there buddy, don't fret. Installing linux for the first time and getting it all up and working the way you want can be a daunting task. I remember my first install... Slackware linux killed my inner child. But i promise you will get better, and then you will look back on all the frustrations and laugh. 

As for your xorg setting, my best advice is to boot into safe mode on startup (command line only) 

issue the command ```
sudo dpkg-reconfigure xserver-xorg
```

this will take you through an automated configuration mode that will reset all of your settings to workable versions. Not a bad idea to make a backup of your xorg.conf once you get back into gnome either. that way next time it happens you can just ```
sudo mv xorg.conf.bak xorg.conf
``` of course making sure that you supply the path along with it. 

What I find that i have the most problems with when i do this configuration is the horizontal and vertical sync rates of my monitor, so google your monitor on a working comp and make sure you know all the suported resolutions etc... 

hope this helped! I know i've had to do this operation a dozen times myself

---

### Post by MountainX on 2008-01-21
Thanks for the tips. I had backed up a good version of xorg.conf, so I just copied it over as you suggested. However, that didn't solve the issue. 

What I ended up doing was uninstalling my nVidia driver using Envy and then reinstalling it again (also using Envy). I saw somewhere that there is something related to kernel binding... could it be that a new version of the kernal was in those automatic updates? What log file can I check to see which updates were applied?

Anyway, I'm in business now, but I would like to understand why I had to uninstall my nvidia driver and then reinstall the same driver again after doing the automatic updates.

---

### Post by damoek on 2008-01-22
Well, I'm certainly no guru... Just a guy who has had his fair share of linux related problems and kept a truckin' 

I know that automatic updates will install kernel updates, but I don't know why that would break your 3rd party driver. 

glad I could be of some help...

---

