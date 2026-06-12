---
title: "Oh, No! Not Again: Lost GNOME"
date: 2007-02-09
forum: Desktop Environments
---

### Post by lakelovers on 2007-02-09
Well, again I was trying to recover my lost audio following the "Comprehensive Sound Problem  Solutions Guide." After uninstalling and reinstalling Alsa stuff per the guides intructions, It said it the Ubuntu Desktop may be lost and to "sudo apt-get install gdm ubuntu-desktop,"  which I did and got a bunch of errors:

pkg: error processing gnome-applets (--configure):
 subprocess post-installation script returned error exit status 1
Setting up nautilus (2.14.3-0ubuntu1) ...

dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on gdm; however:
  Package gdm is not configured yet.
 ubuntu-desktop depends on gnome-applets; however:
  Package gnome-applets is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gdm
 gnome-applets
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

That happened on a second or third try after receiving the message that said (in part) only one display manager can manage a given Xserver. . . please select which dispaly manager should run by default." Then, "edit each of their init scripts in /etc/init.d."

Okay,  I haven't a clue. . .

What have done and what can I do to get my GNOME back? This sound thing has got me baffled. I lost it over a month ago and I've blown my top trying to fix it but seems that every time I get into the Alsa thing I lose the GNOME and still don't get my sound back. The intergrated sound on my Dell 2300 works fine. I ran a diognostic CD to prove the on board sound and it worked perfectly. So the problem is in Alsa/ Ubuntu. Can anybody get me out this corner.
Jerry

---

### Post by lakelovers on 2007-02-10
It's amazing. GNOME is back and I did nothing to help it. I shutdown the computer every night. When I booted this morning GNOME was back in its fully glory. This is the second time Ubunut seemed to have corrected itself. The first was when I struggled for serveral days to get Sbackup working. Then one morning when I booted up it was working. Rebooting was seem to  have been the solution each time but the fact is I rebooted each time I reinstalled the apps or edited their config files. How it happens I don't know but I'll accept all the good thing Ubuntu delivers.

I still have no sound, however. Any ideas, anyone?

Jerry

Well, I thought it was recovered but it's not totally backup. When I exited to reboot I found the the exit screen was missing a couple of icons (shutdown and restart). I clicked where shutdown should be and it did shut down but not in the normal way. On reboot, I got a strange screen of vertical lines which was replaced by the normal log in screen. So, it's working but something still needs fixing. Maybe I'll try re-intalling GNOME.

---

