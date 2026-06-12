---
title: "[HOW TO] Work between two monitors"
date: 2007-12-07
forum: Dell  Ubuntu Support
---

### Post by el escocés on 2007-12-07
[CENTER]**[COLOR=Red]ONLY APPLYS TO INTEL GRAPHIC USERS[/COLOR]**
[/CENTER]
 
I've found a very neat app that has proved very handy to me.

I have my dell connected to an external monitor with the lid closed, my pre-gutsy problem was that when I had to go to a meeting I disconnected the monitor and had to reset X to get the screen working.

That was using the i810 driver, now in Gutsy you can use the intel driver, which gives you the possibility to use the xrandr app.

To change to the intel driver run 

```
sudo dpkg-reconfigure xserver-xorg
```When it asks for the driver select 'intel' all the other options should remain the same as you are using the current configuration settings.

Reboot.

In terminal run

```
xrandr -q
```This will display the possible config setting for your display(s).

In my case when I want to switch from my monitor to my laptop I run this command

```
xrandr --output VGA --off --output LVDS --mode 1280x800
```and back to the monitor

```
xrandr --output LVDS --off --output VGA --mode 1280x1024
```We can now make a script that detects what is connected and turn on the necessary display :

```
#! /bin/bash

if xrandr -q | grep -q  "VGA connected"; then
  xrandr --output LVDS --off --output VGA --mode 1280x1024
else
  xrandr --output VGA --off --output LVDS --mode 1280x800
fi
```Be sure to disable sleep mode when the lid is closed System>Preferences>Power Management 'When laptop lid is closed' Do nothing.

Make the script executable

```
sudo chmod +x FILENAME.sh
```Then we can assign a shortcut key to run this script: [http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/)

PS. I also run this script on startup (Preferences>Sessions>Startup Programs)

hth!

---

### Post by sciurus on 2007-12-07
It's great, isn't it? My only concern is does dpkg-reconfigure add a "virtual" line? For more info, see [here]("http://ubuntuforums.org/showthread.php?t=617934").

---

