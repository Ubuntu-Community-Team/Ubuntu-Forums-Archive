---
title: "Unity application switcher problems after Nvidia driver activation"
date: 2013-12-26
forum: Desktop Environments
---

### Post by ronenc2 on 2013-12-26
Hi all,

I am running Ubuntu 12.04 with Unity. I activated nvidia_331 driver earlier. After rebooting the application switcher (ALT+TAB and ALT+~) started having some problems:

1. It didn't group windows of the same application together
2. The icons are very small
3. It doesn't show a preview of the window anymore

There were other changes too, such as the status bar not being transparent any longer. I decided to deactivate the Nvidia driver, and after rebooting 
the resolution was very low. This was fixed following the directions in [http://ubuntuforums.org/showthread.php?t=1659556](http://ubuntuforums.org/showthread.php?t=1659556)

The other problems still persist. I would really appreciate any help. Thank you!

---

### Post by vanadium on 2013-12-28
After activating the nvidia driver, your Ubuntu installation probably reverted to running Unity-2D. It appears that after removing the driver, the system is still using Unity 2D. Log-out of the system, then before loging in, see whether you can change the desktop again to the 'normal' version of Unity (look for an option on the log-in screen). This should then restore the behaviour as it was before.
b.t.w., is your system fully updated?

---

