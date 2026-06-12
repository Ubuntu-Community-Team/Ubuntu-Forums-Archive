---
title: "MATE auto-login does not work"
date: 2020-10-03
forum: Desktop Environments
---

### Post by mark bower on 2020-10-03
Ubuntu 20.04.1LTS  kernel 5.4.0-48  Mate 1.24.0

The problem is that extra steps are necessary to get Mate to launch.  I installed Mate via "sudo apt-get install ubuntu-mate-desktop" and set it to Auto Login.  It works nicely once I get into it.  

Sequence for 1st boot after MATE is installed
-  boot with the red Gnome 3 screen
-  click the Gnome login "person icon"
-  the Gnome password box opens and an icon is displayed in lower rt of screen
-  select the icon which gives choices for MATE, Gnome, Wayland
-  select MATE
-  login with password
-  boot into MATE completes
Sequence after 2nd and subsequent boots
-  boot, see large green MATE logo in center of screen with dot action
-  MATE green screen is replaced by "red Gnome login screen" with the "person icon" and an icon is displayed in lower rt of screen
-  now disregard the lower right icon
-  enter password and press return
-  Desktop will open with MATE green screen


And of course, what is desired, is that boot goes directly to MATE desktop with no further action between boot and MATE display.  Fiddling, it appears that MATE does not override some Gnome settings.  The crux of the problem is that if I turn auto-login off in Gnome, then I cannot get into MATE.

I am guessing there is a simple fix &#8211; please offer that guidance.

---

### Post by mark bower on 2020-10-06
I solved the problem by determining which display manager was being used, then editing the display manager's file.

First, boot into MATE

Second, use the following to determine what display manager the system is using; my system showed gdm3:
```
cat /etc/x11/default-display-manager

```
Third, went to gdm3's custom.conf file with the following:
```
sudo gedit /etc/gdm3/custom.conf
```
Then changed the AutomaticLoginEnable line to True as,
```
AutomaticLoginEnable = True
AutomaticLogin= user
```

---

