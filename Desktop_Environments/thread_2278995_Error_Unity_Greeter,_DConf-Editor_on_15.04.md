---
title: "Error: Unity Greeter, DConf-Editor on 15.04"
date: 2015-05-20
forum: Desktop Environments
---

### Post by maxwellcom on 2015-05-20
On a fresh install of Ubuntu 15.04, I enter the following commands to remove the dots from the login screen:

```
sudo xhost +SI:localuser:lightdm
sudo su lightdm -s /bin/bash
gsettings set com.canonical.unity-greeter draw-grid false
exit
```

On the last command, I receive the following error:  

> dconf-WARNING **: failed to commit changes to dconf: Error spawning command line 'dbus-launch --autolaunch=b4a2ccca5550480a94721c8cffacce02 --binary-syntax --close-stderr': Child process exited with code 1

The dconf-editor shows that the com.canonical.unity-greeter draw-grid is set to false, and the login screen still shows the dots.

Can anyone identify what's causing the error message and how to actually remove the login screen dots in 15.04?

---

### Post by dino99 on 2015-05-20
where have you seen dots with lightdm ? Should be the ones of plymouth i suppose

---

### Post by jamesfturner on 2015-05-20
Although it doesn't display any user interface, gsettings needs access to your X display server in order to work. Try replacing the first of your commands with:

xhost +

(no need to prefix with 'sudo')

This disables X access control (so that any local user can open an application on your display, as well as read details of what you're doing), so as soon as you're finished you should reverse it with:

xhost -

If you're going to immediately log out (in order to admire your non-dotty login screen) then that will also return the access control settings to normal.

---

### Post by maxwellcom on 2015-05-20
Thanks, that modification did the trick:

```
xhost +
sudo su lightdm -s /bin/bash
gsettings set com.canonical.unity-greeter draw-grid false
exit
```

It makes sense that for "lightdm" to run the gsettings app, I'd need to disable X access control.  Who knows why I had the original commands saved over from a 14.04 install...

---

### Post by mc4man on 2015-05-20
I was never that keen on the su workaround to setting this preference to the greeter when it stopped being available to the admin user some time ago.

Another way to do this is thru an override file / schemas
(the 3rd line may be unneeded but no harm in inc.
To do, using nano
Open a terminal > 
```
sudo nano /usr/share/glib-2.0/schemas/50_unity-greeter.gschema.override
```
In nano copy & paste this in
```
[com.canonical.unity-greeter]
play-ready-sound = false
background-color = "#000000"
draw-grid = false
```
Save & exit nano

(- to save & exit nano if not familiar with
ctrl+o
press enter on keyboard
ctrl+x

Then to finish, in a terminal, this command should complete without any comment or error in the terminal - 
```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas/
```
Then reboot

---

