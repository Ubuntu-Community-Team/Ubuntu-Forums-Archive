---
title: "What's going on? No desktop icon, only wallpaper after update."
date: 2011-10-18
forum: Desktop Environments
---

### Post by adxgrave on 2011-10-18
Hi all,

This must be the most horible security update ever. Never cross my mind to check what being update because it's so reliable that nothing appeared change until just now. What has a simple update done to my netbook lucid, I have no desktop icons and side menu only wallpaper. Clicking on the ubuntu logo on the top left didn't do nothing. WTH? I have to run alt+f2 google-chrome to post this. 

How can I roll back the last update or fix whatever this is? Run dpkg-reconfigure xserver-xorg, nothing. Help please.

Thanks.

Edit: This must have something to do with xorg. I remember it's on the top list of what's being update. I tried running xbmc which is all fine before and now it give me "XBMC needs hardware accelerated OpenGL rendering. Install an appropriate graphics driver."

---

### Post by randywilharm on 2011-10-19
sudo dpkg-reconfigure -phigh xserver-xorg


Try that...I too have an Nvidia card that will do wonders with linux
but you have to learn how to install the drivers as root:

[http://www.nvidia.com/Download/index.aspx?lang=en-us]("http://www.nvidia.com/Download/index.aspx?lang=en-us")

---

### Post by adxgrave on 2011-10-19
I don't have nvidia. This is ubuntu lucid netbook remix on hp mini 210 with intel graphics. Should work out of the box. Any other tips? Still no go.

---

### Post by captain_rob on 2011-10-19
Same problem here after recent update (Compiz?).

---

### Post by MelissaCutler on 2011-10-19
I think I am having the same problem.  I don't know how to fix it, but there is a very simple way of getting things working in the mean time.

The problem is that the "netbook remix" graphical user interface no longer seems to load properly after an update this morning.  But it is possible to load a more conventional gnome interface on the same machine instead (I think it is already installed by default and just needs to be selected at start up).

When you are at the login screen, click on your username; before you enter your password, look down at the bar at the bottom of the screen.  You should see a menu of "sessions" select "Gnome" or Gnome fall back or something like that instead of Netbook remix.  That should get you into a regular Gnome interface.  It's working for me.

Hopfully the Netbook remix problem will be fixed in a fresh update soon.

Hope that helps,

Melissa

PS: Please let me know if you find this helpful

---

### Post by adxgrave on 2011-10-19
Please refer to this thread for solution. [http://ubuntuforums.org/showthread.php?t=1864489](http://ubuntuforums.org/showthread.php?t=1864489)

---

### Post by MelissaCutler on 2011-10-21
Thanks adxgrave,

but the thread in that link makes so little sense to me that I can't even confirm that I am experincing the same problem as they are describing.

"**compiz**" and "**xorg**" are words that mean nothing to me.  They appear to be describing problems related to a GNOME interface. My problems are with a Unbuntu Netbook Edition interface - I have switched to a Gnome interface instead and it is working perfectly (as far as I can tell).

I am using the Netbook remix of  Ubuntu 10.04 LTS "Lucid Lynx" which is similar to the systems described by some of the people in that thread.

---

### Post by MelissaCutler on 2011-10-21
The developers have released an update which fixes the problem.

Use the update manager, then restart and everything should be back to normal.  If you can't get to the update manager graphically then you can try the following:


Option 1: open a terminal and using the command:
sudo apt-get update
(You'll be prompted for an admin password)


Option 2:
press Ctrl + Alt + F1
enter the username and password associated with an administrative account
type the command:
sudo apt-get update
(You'll be prompted for an admin password)

Option 3:
Press Alt + F2
check the letter box marked "run in terminal"
Enter the command in the box:
sudo apt-get update
When you run it a terminal will open and you'll be prompted for a password.

---

### Post by adxgrave on 2011-10-23
Thanks for the instruction melissa, funny thing is I've downgrade the xorg-core and xorg-common to the last working version. Only today I have the courage to update again as I saw those package have jumped from xx-ubuntu8 to xx-ubuntu10. Kudos to the devs, it's pretty darn fast.

Problem solved.

---

