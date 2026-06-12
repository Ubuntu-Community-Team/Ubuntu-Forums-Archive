---
title: "Can't get 1280x1024 resolution"
date: 2011-10-19
forum: Desktop Environments
---

### Post by tnsmart on 2011-10-19
I recently installed Ubuntu 11.04 on a Gateway E-4500 desktop computer ([http://support.gateway.com/s/PC/E4500/1008522/1008522sp3.shtml]("http://support.gateway.com/s/PC/E4500/1008522/1008522sp3.shtml").  Everything seems to be working fine, except that I cannot get the 1280x1024 resolution native to the monitor.   When I go to the monitor settings, the maximum resolution available is 1024x768.

I have had the resolution at 1280x1024 three times: right after installation, after completing several updates after installation, and after running these three commands:
sudo apt-get remove --purge xserver-xorg
sudo apt-get install xserver-xorg
sudo dpkg-reconfigure xserver-xorg
(found here: [http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html]("http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html")) and reinstalling ubuntu-desktop through Synaptic Package Manager.

But when I restart, it reverts back to 1024x768.

I have no file xorg.conf file at /etc/x11/ and am having trouble generating one.  Every time I run "sudo etc init.d gem stop," so that I can run the command to generate the file, the GUI quits, but I never get to a command prompt.  I get stuck at something like "Checking battery state…" or something else.

Any ideas how I can fix this and get my resolution to stay at 1280x1024?  Any help is appreciated.  Thanks.

---

### Post by fantab on 2011-10-20
I had the same problem with my other monitor. I solved it following the [instructions here]("http://forums.linuxmint.com/viewtopic.php?f=49&t=76085#p444558"). 
See if it works.

---

### Post by tnsmart on 2011-10-21
Yes!  Thank you!  The link your provided solved my problem, for the most part.

I ran these commands:
```
mkdir ~/Scripts
gedit ~/Scripts/fix-resolution.sh
```saved this in the document that opened:
```
#!/usr/bin/env sh
xrandr --newmode "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
xrandr --addmode VGA1 "1280x1024_60.00"
xrandr --output VGA1 --mode "1280x1024_60.00"
# done
```and ran these commands:
```
chmod +x ~/Scripts/fix-resolution.sh
sudo ln -s ~/Scripts/fix-resolution.sh /etc/X11/Xsession.d/45fixresolution
```It now loads 1024x768 at the login screen, but switches to 1280x1024 after logging in for both users.

The only problem I have left is that it seems to delay the login process.  Any way to fix this?  Thanks again.

---

