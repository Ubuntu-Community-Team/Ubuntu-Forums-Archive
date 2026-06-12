---
title: "gnome desktop on ubuntu server"
date: 2007-01-13
forum: Desktop Environments
---

### Post by dignick on 2007-01-13
I've installed x and gnome on ubuntu server using
apt-get install x-window-system-core xserver-xorg gnome-desktop-environment
(see here: [http://www.ubuntuforums.org/showthread.php?t=186298](http://www.ubuntuforums.org/showthread.php?t=186298))

I've had it working a couple of days.  Now, when I start up and enter startx, it begins to start with the grey screen and cross cursor, but then a grey box appears top left, and nothing else happens.  If I quit I can see a few errors: 'cannot open device /dev/wacom no such file or directory' and after several of those duplicate errors, 'Could not init font path element /usr/share/fonts/x11/ (ttf/) (otf) (cid/) removing from list!' followed by 'freefontpath: fpe "/usr/share/fonts/x11/misc" recount is 2, should be 1, fixing.'

I get this every time I try to start x now.  I reinstalled and reconfigured x once before, and that worked, but it doesn't this time.  Any ideas?

Also, when I get into gnome, run a terminal window and enter 'sudo gedit' with or without a file to open, I don't get a password prompt and it doesn't open.  I have to ctrl+c to get out of it.  I've tried 'gksudo gedit' but it didn't work properly for a reason I can't recall. (see here: [http://ubuntuforums.org/archive/index.php/t-77283.html](http://ubuntuforums.org/archive/index.php/t-77283.html))

*Another thing I would like to do when I've solved both of those problems is remove all non-essential stuff that came with gnome-desktop, eg evolution.  When I try removing them it says I can't due to dependencies.  Is there a way I can do this?* **Answered**

Thanks for help.

---

### Post by tturrisi on 2007-01-13
Not sure about Ubuntu, I use Etch, but when I install I install xorg and gnome-core instead of gnome-desktop-environment.  Gnome-core is gnome w/out the bloat. 

Here's the list of Ubuntu Gnome packages for edgy:
[http://packages.ubuntu.com/edgy/gnome/](http://packages.ubuntu.com/edgy/gnome/)
(just do apt-get install gnome-core instead of the full gnome-desktop-environment and add desired packages as you see fit, i.e. just the ones you want.

---

### Post by dignick on 2007-01-13
Thanks - that's answered my 3rd question!  Great support experience with Ubuntu.  Better than commercial. :)

---

### Post by dignick on 2007-01-14
Anyone any idea with the 1st 2 problems?

Thanks.

---

