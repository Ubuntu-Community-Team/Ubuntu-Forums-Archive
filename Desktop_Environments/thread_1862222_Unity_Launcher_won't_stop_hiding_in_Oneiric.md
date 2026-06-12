---
title: "Unity Launcher won't stop hiding in Oneiric"
date: 2011-10-16
forum: Desktop Environments
---

### Post by jswhite on 2011-10-16
Just upgraded to Oneiric from Natty, and have a minor Unity annoyance. I hate the whole "hiding launcher" thing with a burning passion. I just want the stupid thing to stay on the screen and quit running away. I have downloaded compizconfig-settings-manager, checked the box for the Unity plugin, and changed the "Hide Launcher" setting to "Never." That worked fine in Natty. It appears to do nothing in Oneiric, as the launcher continues the same "run and hide" behavior it did before I changed the setting.

I have changed the setting back and forth three or four different times, occasionally with logouts/reboots in between, and the launcher just refuses to stay put. Help, please, before I stab my computer?

---

### Post by Krytarik on 2011-10-16
Please see my earlier post here:

[http://ubuntuforums.org/showthread.php?p=11349787#post11349787](http://ubuntuforums.org/showthread.php?p=11349787#post11349787)

Regards.

---

### Post by jswhite on 2011-10-16
Problem solved (finally). After looking through the posts you linked to, checking the links from there, etc., I eventually narrowed the problem down. I had for whatever reason two kernels installed, with the headers for only one of them. When the fglrx package was compiling the kernel module, there was a mismatch between the kernel I was using and the kernel headers that were being linked to. Once I got that all sorted out, the fglrx install went off without a hitch and it's now properly using my graphics card.

Thanks!

---

