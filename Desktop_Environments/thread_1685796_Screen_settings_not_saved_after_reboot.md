---
title: "Screen settings not saved after reboot"
date: 2011-02-11
forum: Desktop Environments
---

### Post by richaustin on 2011-02-11
Hi all

I know this has been covered before but I can't find a resolution to the issue. Kubuntu simply refuses to save the screen settings, and each time I reboot it returns to 1440 x 900. The correct resolution should be 1920 x 1080.

KRandr shows 1440x900 (auto) in its drop down Size field. I've set krandr to load on startup so that I can set the correct resolution but of course this means I have to set the panel size as well. I've only recently installed KUbuntu and it's great except for this issue. Surely there must be a simple fix? I'm not a noobie and have about 4 years experience on Ubuntu / openSuse etc.

Thanks in advance for any help / pointers / sympathy etc.
Rich

---

### Post by richaustin on 2011-02-11
Solved this finally. The solution was as follows:

From the command line enter:

cd /etc/kde4/kdm/
ls

This should show a number of files, one of which is Xsetup. Now enter:

sudo kate Xsetup

You can replace "kate" with whatever editor you prefer. Now add a line like this to the file that opens:

xrandr --output VGA-0 --mode 1920x1080

Make sure of course that you change the VGA-0 to the correct display for your system. Also, obviously, change 1920x1080 to the resolution you require.

If you don't know what your display name is:

hold down the Alt key and press F2. Type "krandrtray" without the quotes.

This will put an icon of a monitor in the system tray near the clock. Click on the icon and it will show you the name of your display in the right hand side of the window.

HTH someone else.
Rich

---

### Post by adsp on 2011-11-18
It doesn't work for me (although I appreciate it's been more than 2 years since this solution was posted, I'm now on 11.10, kubuntu). And I tried playing with startupconfig (in ~/.kde/share/config), also xorg.conf...

The only thing I could do was to add the changes to ~/.profile

xrandr --output VGA1 --mode 1920x1080
xrandr --output LVDS1 --off

That does the trick, the only downsize is that if I don't have the monitor attached (laptop standalone) the (laptop) screen will remain off; so the only thing I can do is to enter a text terminal (Ctrl-Alt-F1...) and revert the changes to .profile :-(

Any other idea?

Adrian

PS. I searched the forum and it doesn't seem to be much recent discussion on this topic. Am I that unlucky to have this problem? Could it be upgraded to kubuntu 11.10 (rather than a clean install)? I mean it is possible that I changed something relating graphics some years ago and I don't remember and the upgrade didn't touch files modified manually...

---

