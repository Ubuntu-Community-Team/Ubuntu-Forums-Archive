---
title: "Applets Failing To Load + Segfaults"
date: 2010-05-04
forum: Desktop Environments
---

### Post by franticpedantic on 2010-05-04
Hi all,

Out of the blue, when I booted ubuntu I get a bunch of windows saying "The panel encountered a problem while loading: OAFIID:GNOME_ShowDesktopApplet", with a bunch of others(5) besides ShowDesktopApplet.  I am able to launch a terminal, and I do have the taskbar at the top, although the bar at the bottom that holds the windows is blank, so when I minimize a window it disappears.  Furthermore, when I try to launch most applications (firefox for example) it segfaults.

I have tried several things to fix this.  I have googled the error but it seems to be common but general issue, and a lot of the solutions that worked for others didn't work for me.  I tried deleting the gconf, gnome, and gnome2 folders in my home directory.  I tried deleting a bunch of the gnome folders (although I might have done this wrong, I was confused as to which ones). 

I have also tried to use apt-get and dpkg to re-install ubuntu-desktop and gnome-applets.  However, when I try 

apt-get install ubuntu-desktop

I get errors regarding 

/var/cache/apt/archives/gnome-applets_2.28.0-0ubunt2_amd64.deb

I tried

dpkg --configure -a

and interestingly I get

Package gnome-applets is not installed.

When I try to use apt-get to install it, that same pesky problem pops up 


error processing /var/cache/apt/archives/gnome-applets_2.28.0-0ubunt2_amd64.deb (--unpack)
  subprocess new post-removal script returned error exist status 245
  sub process /usr/bin/dpkg returned an error code(1)

This file has been popping up with regards to a lot of the solutions suggested I see.  Any new ideas?  Thanks!

---

### Post by dino99 on 2010-05-05
redownload and reinstall the package from:

[http://packages.ubuntu.com/lucid/gnome-applets](http://packages.ubuntu.com/lucid/gnome-applets)

note: select the good distro if yours is not lucid

---

### Post by franticpedantic on 2010-05-05
Thanks a lot for the tip, I will try this as soon as I get home from work.

---

### Post by franticpedantic on 2010-05-05
Thanks again, but unfortunately this did not resolve the situation.  Instead I get an error regarding the package I downloaded.  When I tried just re-installing everything, I got 'package is in a very bad inconsistent state'.  

I tried following this advice:
[http://ubuntuforums.org/showthread.php?t=813809](http://ubuntuforums.org/showthread.php?t=813809)

regarding that, but I still get errors.  It also complains about missing gnome-applets-data, but I don't think that is the source of the problem.  The error I still get is 

subprocess new post-removal script returned error exist status 245.

I tried removing ubuntu-desktop to, problem always goes back to gnome applets.   

dpkg:  error processing gnome-applets (--configure)

It looks like I just have to re-install :-/  If anybody else had some tips though, that would be extremely appreciated and I will definitely try them.

---

