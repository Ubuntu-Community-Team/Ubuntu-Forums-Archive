---
title: "Unity Doesn't Load on Login"
date: 2011-10-25
forum: Desktop Environments
---

### Post by sufjanfan on 2011-10-25
Hello all. I recently upgraded to 11.10, used Unity for a while, and kinda got used to it, but I wanted to try some alternatives. I installed XFCE and LXDE with "sudo apt-get install xubuntu-desktop" and "sudo apt-get install lubuntu-desktop". I noticed this left me with a bit of a mess (XFCE loading screen, LXDE login manager, too many applications, etc.) and decided to uninstall both via the commands found on [http://psychocats.net/ubuntu/puregnome](http://psychocats.net/ubuntu/puregnome).

Now when I login to a standard Ubuntu session I see nothing except a movable cursor and my background. There is no bar at the top and there is no Unity dock at the side. Ctrl-Alt-T does not work, but Ctrl-Alt-Delete gives me a logout dialog.  Unity 2D does work, but for some odd reason it's always been slower than the standard Unity.

Steps I have tried:
1. Opening up Compiz Config Settings Manager and ensuring the Unity plugin is enabled.
2. Reseting Compiz to defaults.
3. "unity --reset"
4. "sudo apt-get install --reinstall ubuntu-desktop"

My guess is that some script buried in the login process is attempting to load some other desktop. I've taken a few peeks into a few files, but haven't changed anything or found anything suspicious-looking. I'd like a solution that simply resets login parameters to defaults if possible, in case anything else behind the scenes is screwed up.

Thanks in advance.

---

