---
title: "What desktop environment should I get into?"
date: 2009-09-09
forum: Desktop Environments
---

### Post by mrcoulson on 2009-09-09
I'm very new to Linux and have an Ubuntu server.  To this point, I've done all configuration with CLI, but I feel like I need to have the ability to fall back on a GUI.  I know it's not best to run a server with the GUI, but I'd really love one just for a few weeks while I'm learning my way around.  Don't you ever think, "Man, if only I just had a mouse right now!"?  Sometimes I do.  It would be a nice comfort when repeated attempts at doing it in CLI are not working.

So, what is a good and lightweight desktop environment?  I don't need a lot of extra apps -- just the ability to manipulate some configurations if needed.

And once I install one, does it still start in CLI?  This is what I envision: I can start and stop the GUI as I need it like starting and stopping any other program.  And once I feel like I'm ready to fly without it, I can just remove it.  Reasonable expectations?

Jeremy

---

### Post by ATL™ on 2009-09-09
i'm pretty fond of openbox.

---

### Post by Locutus_of_Borg on 2009-09-09
> **ATL™ said:**
> i'm pretty fond of openbox.

additional vote for openbox

---

### Post by earthpigg on 2009-09-09
additional vote for openbox.

if you want a start-menu-equivelant that will automatically update when you install new software, and other full-blown-desktop functionality... consider LXDE. 

it runs on top of openbox and is the most lightweight of what i personally would consider a 'desktop enviornment'.

> once I install one, does it still start in CLI?

it does _if you want it to_.

when you install openbox/lxde/whatever-you-choose, make sure you use apt-get's --no-install-recommends option and _read what packages it is installing_. make sure none of those packages are a 'display manager'.

gdm
slim
kdm

are a few examples of display managers you want to ensure your WM/DE of choice doesn't install alongisde itself unless you want it to.

a display manager will replace the current CLI-based "login:________ password:_______" thing you have going.

it will be graphical, but from the display manager you can choose to immediately drop *right back down* to the command line.

if you decide you do want one, GDM is ubuntu's default, is freedesktop.org compliant, and requires minimal configuration. once you install a new WM or DE, it will pick up on that and give you the option to start it without any additional configuration.


anything that is freedesktop.org compliant: will usually work completely unmodified and unconfigured (beyond installing/activating/starting it) with lxde, gnome, xfce, and a bunch of others.... but not kde.

---

### Post by mrcoulson on 2009-09-10
Great!

Okay, before I proceed, I have questions about what I've found at [http://icculus.org/openbox/index.php/Help:Installing](http://icculus.org/openbox/index.php/Help:Installing).  Do I need to install all of those packages under "Dependencies in Ubuntu and Debian" before doing "apt-get install openbox"?  I just don't want to screw something up!  A fourth OS reinstall in one week would not be my idea of success.

Jeremy

---

### Post by mrcoulson on 2009-09-10
Sorry if my questions seem retarded, but I've only ever used Windows and Mac OS where it's all installers or executables or dragging a file from the mounted disk image to Applications and enjoying the day.  I get nervous when I read things like "Once you have the above dependancies installed, you are ready to build Openbox. Untar the Openbox archive and from inside the source tree, run..."

Jeremy

---

### Post by earthpigg on 2009-09-10
> Do I need to install all of those packages under "Dependencies in Ubuntu and Debian" before doing "apt-get install openbox"? 

hell no you dont. this isn't [slackware]("http://en.wikipedia.org/wiki/Slackware#Dependency_resolution"), its ubuntu.

and ignore that crap about 'untaring' this and 'building' and 'source trees' and all the rest.

thats for people compiling from source.

thats for people _*not*_ using an easy-to-use distribution that has already done the building from source for you.

heed my advice: unless there is a very compelling reason not to, install everything from _apt-get install_, every time always no matter what. ubuntu put those repositories there for a reason!

---

### Post by mrcoulson on 2009-09-11
apt-get every time!  Yessir!

I'm going to give this a shot now!

Jeremy

---

### Post by earthpigg on 2009-09-11
good luck to you, sir :D

---

