---
title: "Hardy: Window manager not starting, gnome"
date: 2008-04-28
forum: Desktop Environments
---

### Post by deadsea on 2008-04-28
When I log into gnome via GDM, the window manager does not start.  New applications appear on the screen without decoracition and no way to position them or switch between them.

I can get to a console and type "metacity" and metacity starts up and improves the situation.  However, next time I log in I see the same behavior.  Even so, the screensaver comes on and freezes the desktop and I have to ctrl-alt-f1 to a terminal and kill gdm.

I suspect that it is because I do not have the entire gnome-desktop-environment installed.  I removed some applications at some point before I upgraded from gutsy to hardy.  I figured I could fix it with apt-get but I have this problem:
[FONT="Fixedsys"]$ sudo apt-get install gnome-desktop-environment
[sudo] password for steveo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnome-desktop-environment: Depends: gnome-keyring-manager (>= 2.20.0) but it is not installable
E: Broken packages[/FONT]

Anybody have any suggestions?

---

### Post by scragar on 2008-04-28
for some reason package doesn't exist on hardy, but the gutsy one works fine, download it, then run:
```
dpkg -i **PATH/FILENAME**
```

download via: [http://packages.ubuntu.com/gutsy/gnome-keyring-manager](http://packages.ubuntu.com/gutsy/gnome-keyring-manager)

---

### Post by deadsea on 2008-04-28
Thanks, I got gnome-desktop-environment fully installed now.  I also had to manually download liblaunchpad-integration0 which was a requirement for gnome-keyring-manager. 

Now to see if that fixes the window manager problem.

---

### Post by scragar on 2008-04-28
you could have used:
```
sudo apt-get install -f
```
to fix the dependencies, but installing them manualy is OK as well I guess. :P

---

