---
title: "Ubuntu 10.04, problem with gnome/x (?)"
date: 2010-12-23
forum: Desktop Environments
---

### Post by nawie on 2010-12-23
Hello


My ubuntu machine is behaving strangely. Since a couple of days ago all i get when i boot it up is:

[http://petar.se/img/ubuntu.png](http://petar.se/img/ubuntu.png)

I have tried to stop and restart gnome without any success (nothing happens). When i try to run gnome by simply typing "gdm" in the terminal i get:

gdm-binary[1975]: WARNING: Unable to find users: no seat-id found
gdm-binary[1975]: WARNING: GdmDisplay: display lasted 0.049479 seconds
gdm-binary[1975]: WARNING: GdmDisplay: display lasted 0.049322 seconds
gdm-binary[1975]: WARNING: GdmDisplay: display lasted 1.593274 seconds
gdm-binary[1975]: WARNING: GdmDisplay: display lasted 1.242075 seconds
gdm-binary[1975]: WARNING: GdmDisplay: display lasted 1.241419 seconds
gdm-binary[1975]: WARNING: GdmDisplay: display lasted 1.242688 seconds
gdm-binary[1975]: WARNING: GdmLocalDisplayFactory: maximum number of X display failures reached: check X server log for errors.

I can run some applications like gedit and nautilus manually. I haven't done anything for this to happen since I haven't been at home.

---

### Post by nawie on 2010-12-24
I solved the issue. The computer used to be connected to a TV with HDMI, but it had been disconnected for some reasons and when ubuntu booted up without any displays it didn't really work.

---

