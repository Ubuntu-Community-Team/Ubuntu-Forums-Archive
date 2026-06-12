---
title: "Can't get Ctrl Alt F1 to work in Intrepid Ibex"
date: 2008-12-08
forum: Desktop Environments
---

### Post by GeekLove_JavaStyle on 2008-12-08
Hello All,
Ctrl Alt F1 is not working on my (home) machine.  Instead of getting a prompt, I get an underscore (_).  I hit enter, nothing happens.  I hit Ctrl Alt F7 and I'm back into GNOME, no problem.  I'm running Intrepid Ibex which I upgraded to from Gutsy Gibbon.  

I run 2 32-bit Ubuntu machines, both with nVidia graphics cards.  My work machine works just fine and I was able to upgrade successfully.  My home machine is giving the error.  I want to upgrade my nVidia driver to test out the 180.x beta, but can't even get to a prompt to run the installer.

Does anyone have any advice on troubleshooting this issue?

Thanks in advance!

---

### Post by daqron on 2009-01-29
I was having the same problem today; some update that I absent-mindedly installed wreaked all manner of havoc on X and on my consoles. I couldn't access consoles through CTRL+ALT+F(1-6). Worse, my system kept going into "Low Graphics Mode" every time I booted. 

**These steps fixed both the "low graphics mode" and blank console screen problems:**

1. Download the latest nvidia driver installer script. I've been using this [beta version 180.08]("http://www.nvnews.net/vbulletin/showthread.php?p=1847941") because it addresses a titlebar rendering issue in Intrepid. If you need another version, [you can get it here (maybe?)]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14").

2. Installed OpenSSH so I could connect to my Ubuntu box through my laptop. Since I couldn't get into a proper console on the box itself, this was the only way to shutdown the X server and be able to issue commands.  

3. Via SSH, kill X remotely (i.e., from 2 feet away):
```
sudo /etc/init.d/gdm stop
```

4. This [other post I found]("http://ubuntuforums.org/showthread.php?t=692827&postcount=3") recommended doing this, and I don't know why ... but what the hell:
```
sudo-apt-get install build-essential
```

5. Disable nvidia modules:
```
sudo nano /etc/default/linux-restricted-modules-common
DISABLED_MODULES="nv nvidia_new"
```

6. Install the nvidia drivers (replace the blue with the appropriate directory and nvidia driver version string for you). You don't necessarily need the "-k $(uname -r)" part but it will take care of any potential kernel/compiler incompatibilities.
```
cd [COLOR="Blue"]/path/to/installer-script[/COLOR]
sudo sh [COLOR="Blue"]NVIDIA-Linux-x86-180.08-pkg1.run[/COLOR] -k $(uname -r)
```

7. Follow the instructions on the nvidia installer script.

8. Manually reconfigure the X server (best tip ever, from PmDematagoda in the other post):
```
sudo dpkg-reconfigure xserver-xorg
```

9. Restart! I tried restarting the X server but no dice, still low-graphics mode. After an actual restart I had my full rez back and all my pretty consoles in CTRL+ALT+F(1-6).

I hope this helps.

---

