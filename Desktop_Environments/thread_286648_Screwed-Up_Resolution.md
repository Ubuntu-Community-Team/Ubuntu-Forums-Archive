---
title: "Screwed-Up Resolution"
date: 2006-10-28
forum: Desktop Environments
---

### Post by Caz'ar Xiladys'varion on 2006-10-28
I have installed Ubuntu successfully, but after I start it up, my resolution is stuck at 640x580 and the screen has this really weird split down the middle. There are, like, two mice and part of my screen is copied and it's weird. Anyone know how to fix this?

---

### Post by sylvester_0 on 2006-10-28
1. Access a command line by doing Ctrl-Alt-F1.
2. Login as yourself.
3. Use the command ```
sudo nano /etc/X11/xorg.conf
```
4. Scroll down to near the bottom using the arrow keys. You'll see something called Section "Screen". Then SubSection "Display". Here you will see a list of all of your resolutions and color depths that can currently be used. Assuming the Default is 24 put your resolution right after that in the Modes line. Here is what mine looks like:

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV43 [GeForce 6600 GT]"
        Monitor         "DELL 2405FPW"
        DefaultDepth    24
        SubSection "Display"
                Viewport 0 0
                Depth           24
                Modes           "1280x720"
```

(Although really my correct resolution is 1920x1200 for this monitor. It's a twinview hack.)

Once you have made the appropriate changes, save the file by doing control-x and answering yes. From here you can do either ```
sudo /etc/init.d/gdm restart
``` or just reboot the whole machine. If you mess it up really bad you can always boot into rescue mode to change this file again.

Good luck :)

---

### Post by Caz'ar Xiladys'varion on 2006-10-28
I changed my file to that, but then I got this error message saying the X server couldn't start because "DELL 2405FOW" wasn't found as a screen, so I had to change it back to what I have, which was "Generic Monitor," which still has the same problem. Is there a list of monitors I can look through to change that?

---

