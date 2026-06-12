---
title: "Unity 'crashes' to light-gray windows 95-like theme"
date: 2011-09-18
forum: Desktop Environments
---

### Post by Adam's AI on 2011-09-18
I've set up Ubuntu in VirtualBox and enabled 3D acceleration, but when I log in, it launches Unity with a light gray windows-95 like menu bar at the top. Is there any way I can fix this?

Thanks

---

### Post by Adam's AI on 2011-09-18
I've found I can get the menu-bar looking right by trying this
killall gnome-settings-daemon
gnome-settings-daemon &

from ([http://tombuntu.com/index.php/2011/04/30/how-to-run-unity-in-virtualbox/](http://tombuntu.com/index.php/2011/04/30/how-to-run-unity-in-virtualbox/))

but my file browser still looks like windows 95. Any ideas on how to fix this??

---

### Post by Krytarik on 2011-09-18
This is the related bug report:
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809)

Try this workaround first:
[http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html](http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html)

If this doesn't work, see here:
[http://ubuntuforums.org/showthread.php?p=11253199#post11253199](http://ubuntuforums.org/showthread.php?p=11253199#post11253199)

Hope any of those works!

---

### Post by Adam's AI on 2011-09-19
Thanks for the reply! I will check those out. I have a feeling alot of my issues might be due to virtualbox. Might give VMware Fusion a try.

---

