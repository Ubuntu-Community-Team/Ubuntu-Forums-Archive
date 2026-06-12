---
title: "Ubuntu Hangs Before Login Screen"
date: 2009-05-08
forum: General Help
---

### Post by bluestreek on 2009-05-08
I have been trying to fix my sound for a while now.  I went to the sound page and did the command to remove all these packages relating to ALSA then reinstalled them. 

It said that sometimes this uninstalls gnome desktop or something so I ran a command to reinstall it.

I then rebooted and it wouldn't boot at all.  I rebooted again and it gets to where there would be a login screen and all I see is a spinning cursor, the equivalent the the windows hour glass.

It tired press ctrl-alt-f1 and got a command prompt and did sudo dpkg-reconfigure xserver-xorg.  This didn't help.  I also tried typing startx but this didn't help as obviously its already running.

Any help would be great!

EDIT: 
This is what I did exactly before restarting.
```
(1) Remove these packages
Code:
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

(2) Reinstall those same packages
Code:
sudo apt-get install linux-sound-base alsa-base alsa-utils
[list][*]
VERY IMPORTANT NOTE: Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following
Code:
sudo apt-get install gdm ubuntu-desktop
```

---

### Post by bluestreek on 2009-05-08
I posted in the relevant thread also but I think this is not longer a sound problem :/

---

### Post by bluestreek on 2009-05-08
Any ideas?

---

### Post by bluestreek on 2009-05-08
bump

---

