---
title: "Total Rookie Question"
date: 2007-09-05
forum: Desktop Effects &amp; Customization
---

### Post by ortwein on 2007-09-05
Hi guys,

I'm about to pull out my hair.  I've been trying to install compiz fusion on my system (kubuntu) to absolutely no avail...nothing changes.  I've tried a variety of methods found on this website--nada.  However, I found a recent post about a script (by elemonGW(  that installs CF for you.  I downloaded the script...but now what?   I don't know how run a script at all.

Any help getting this going would be greatly appreciated...and thanks for all the hard work you guys do!

Mark

---

### Post by Inxsible on 2007-09-05
What other guides did you try ?

Installing with Trevino's or Amaranth's repos is pretty straight forward. you add the repos in your sources.list file and then simply update and install

---

### Post by Inxsible on 2007-09-06
For the script you simply  have to make it executable and then run it
cd to the directory where you downloaded the file
```
sudo chmod +x <filename>
```then run the file

---

### Post by ortwein on 2007-09-06
I tried amaranth's...haven't tried trevino's.  

I'm not sure if I did it correctly or not.  I'm using Adept Manager in Kubuntu, and I'm afraid I might not have updated the repo correctly.  Anway, when I did a search in Adept for compiz the same files showed up; there was no difference.  

Additionally, I've tried the installer shell script recently posted here, but don't know how to run it.  It just brings up KATE.

I hate to be such a noob...but I don't know where else to go to learn.

Any ideas where I've gone wrong?

---

### Post by Inxsible on 2007-09-06
if you want to use Trevino's repos this is what you do

```
kdesu kate /etc/apt/sources.list
```add the following lines at the end of the file and then save the file```
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

```then back in the terminal do this```
sudo wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
``````
sudo apt-get update && sudo apt-get install compiz compiz-core libcompizconfig0 compiz-config-settings-manager
```

---

### Post by ortwein on 2007-09-06
Followed your directions.  After running "sudo apt-get update && sudo apt-get install compiz compiz-core libcompizconfig0 compiz-config-settings-manager"
here is an error that popped up at the end of the string:

E: Couldn't find package compiz-config-settings-manager
bonehead@bonehead:~$

Also, should I purge my system of any other installs I've tried?

---

### Post by ortwein on 2007-09-06
Here is some information regarding my current setup:

video card (I have a radeon 9200 pro)

bonehead@bonehead:~$ egrep 'Composite|Section\ \"Device' /etc/X11/xorg.conf -A 10
Section "Device"
Identifier "Generic Video Card"
Driver "vesa"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "DELL E173FP"
Option "DPMS"
EndSection

bonehead@bonehead:~$

Open GL settings

bonehead@bonehead:~$ glxinfo | egrep 'OpenGL|direct'
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
bonehead@bonehead:~$

Compis (I thought I'd uninstalled it...guess not.

ic compiz-extra 0.3.6.1-0ubuntu2 extra third party plugins for compiz
rc compiz-gnome 0.5.5~git20070905+3v1ubuntu0 OpenGL window and compositing manager - GNOM
rc compiz-gtk 0.3.6-1ubuntu13 OpenGL window and compositing manager - Gtk
rc emerald 0.3~git20070717-0ubuntu1~ppa1 Decorator for compiz-fusion
ii kde-style-polyester 1.0-1ubuntu2 Polyester widget style and kwin decoration f
ii kwin-style-crystal 1.0.2-1ubuntu1 semi transparant window decoration for KDE
rc libberyldecoration0 0.2.1.dfsg+git20070318-0ubuntu2 Settings library for plugins - Beryl Project
rc libcompizconfig0 0.5.2-0ubuntu1~ppa2 Settings library for plugins - OpenCompositi
rc libdecoration0 0.5.5~git20070905+3v1ubuntu0 Compiz window decoration library
rc libemeraldengine0 0.3~git20070717-0ubuntu1~ppa1 Decoration engines for compiz-fusion

---

### Post by Inxsible on 2007-09-06
> **ortwein said:**
> Followed your directions.  After running "sudo apt-get update && sudo apt-get install compiz compiz-core libcompizconfig0 compiz-config-settings-manager"
here is an error that popped up at the end of the string:

E: Couldn't find package compiz-config-settings-manager
bonehead@bonehead:~$

Also, should I purge my system of any other installs I've tried?

Maybe the package name is different :( just install the compiz compiz-core and libcompizconfig0 and ccsm should be installed with them

---

### Post by Inxsible on 2007-09-06
Have you had a look at some of the Compiz + ATI threads ?

They could help you out in setting it up to handle Compiz

---

### Post by ortwein on 2007-09-06
I'll check them out...

Are the compiz fusion files that come up with Adept Manager no good or something?   I hear people talking about repositories..but nobody mentions files that come up when you do a standard search in Adept or Synaptic.

Also, does it matter that I'm using Kubuntu instead of Ubuntu?

---

### Post by Inxsible on 2007-09-06
> **ortwein said:**
> I'll check them out...

Are the compiz fusion files that come up with Adept Manager no good or something?   I hear people talking about repositories..but nobody mentions files that come up when you do a standard search in Adept or Synaptic.
Compiz Fusion is not in the standard repos for Feisty. The compiz you see is different from compiz fusion. CF is the one with all the cool effects and stuff. 

The regular compiz that comes pre-installed with Ubuntu, cant do much except rotate cube and a few other effects.

---

### Post by [Alsharifi] on 2007-09-06
hey bro i had alot of problems installing CF with my ATI card to.but now i got it working flawlessly.

i think best thing to do is purge all your compiz files or anything u installed and start fresh with this guide,follow it word for word and u will be set!

[http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)


remember follow carefully!

good luck!


if u have any problems or questions post here.

---

