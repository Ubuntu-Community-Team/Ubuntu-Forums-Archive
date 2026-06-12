---
title: "Desktop effects cause problems after reboot"
date: 2007-07-08
forum: Desktop Effects &amp; Customization
---

### Post by H-Radical on 2007-07-08
Hi all,
After a long struggle, I was able to get my nvidia card (GeForce4 420 Go) working after my Feisty upgrade. Immediately after getting the nvidia driver to work, I tried the desktop effects feature that comes with feisty. I added the lines that compiz required to my xorg.conf and also downloaded compiz-gnome-manager. Everything worked great. After I shutdown the computer and started it again, the nvidia driver loaded, but I saw the gnome splash screen did not go away until I right clicked on it; the laptop power icon, the ethernet icon, and the update manager icons on the gnome panel did not load for 20-30 seconds until after the login; I couldn't open my nvidia x server settings program and the command ```
$ sudo nvidia-settings
``` crashed with a segmentation fault (core dump); of course, there were no desktop effects eventhough I could see they were enabled; finally, in the gnome manager of compiz, when I enabled "GL Desktop" , some of the options were missing (they just didn't show up on the gui where they were supposed to be) and ofcourse there were no effects.
System -> Administration -> Restricted Drivers Manager gave me a prompt saying I need the linux restricted modules package (I know I have it already). ```
$ sudo /etc/init.d/gdm restart
``` gave me a crashed X server without any significant errors that I could diagnose any problems from. So I went through the whole process of uninstalling the NVIDIA drivers and reinstalling it, I restarted X and everything was fine. I enabled compiz and got all the effects and all of the above-mentioned problems were gone. I rebooted and the saga started all over again. The next time after reinstalling the nvidia drivers, I didn't enable desktop effects and voila! Everything worked after a reboot. More details about my graphix card and xorg.conf can be found at [http://ubuntuforums.org/showthread.php?t=492441]("http://ubuntuforums.org/showthread.php?t=492441")
Does anyone know what compiz is doing to my system to cause this and what i can do to use desktop effects without any problems?

Cheers

---

