---
title: "Error detecting shell when launching Gnome Tweak Tool"
date: 2017-08-03
forum: Desktop Environments
---

### Post by John_Rose on 2017-08-03
Hello,
  
  I have just upgraded from Ubuntu 12.04 LTS to Ubuntu 14.04 LTS running GNOME. The upgrade went smoothly (this was a different computer from the one on which I reported an interrupted upgrade last week).
 
  My problem is that I cannot tweak the themes with gnome-tweak-tool. When I load gnome-tweak-tool I get the following error messages:
  
  WARNING : Shell not installed or running
  INFO    : GSettings missing key org.gnome.nautilus.desktop (key computer-icon-visible)
  WARNING : Error detecting shell
  Traceback (most recent call last):
   File "/usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_group_shell_extensions.py", line 284, in __init__
     raise Exception("Shell not running or DBus service not available")
  Exception: Shell not running or DBus service not available
  WARNING : Shell not running
  
 The tool windows are available but theme parameter changes in the Appearance tab do not work (you can write them in, but no effect and the default is restored upon exit).
  
 The same problem occurs whether logged in with Metacity, Compiz, Ubuntu or GNOME.

    [SIZE=2]When I run:[/SIZE]
 [SIZE=2]"if pgrep gnome-shell; then echo GNOME shell is running; else echo Nope not running;fi[/SIZE]" [SIZE=2]it answers "[/SIZE][FONT=Liberation Mono][SIZE=2]Nope not running"[/SIZE][/FONT]
  
  [SIZE=2]When I log in as another user with root privileges, the same error and gnome-tweak-tool disfunction occur.[/SIZE]

      [SIZE=2]I tried the following recommended fixes, none of which works after rebooting:[/SIZE]

 * sudo apt-get install --reinstall ubuntu-desktop
* sudo apt-get install xserver-xorg-video-intel [the reply is that the most recent version is already installed]
* sudo rm -fr .cache/* 
   [FONT=Liberation Serif][SIZE=3]* [/SIZE][/FONT][FONT=Liberation Serif][SIZE=3]reinstalling gnome-shell and gnome-tweak-tool with ppa "g[/SIZE][/FONT][FONT=Liberation Serif][SIZE=3]nome3-team/gnome3" as recommended in 2012 ([https://ubuntuforums.org/showthread.php?t=2029427](https://ubuntuforums.org/showthread.php?t=2029427)[/SIZE][/FONT][COLOR=#000080][FONT=Liberation Serif][SIZE=3])[/SIZE][/FONT][/COLOR][FONT=Liberation Mono][SIZE=2]
sudo add-apt-repository ppa:gnome3-team/gnome3[/SIZE][/FONT]
sudo apt-get update
sudo apt-get install gnome-shell gnome-tweak-tool
[FONT=Liberation Mono][SIZE=2]sudo apt-get update[/SIZE][/FONT]
[FONT=Liberation Mono][SIZE=2]sudo apt-get dist-upgrade

[/SIZE][/FONT]   Maybe unrelated, but I also at another time got a non-fatal system error message citing at-spi2-registryd (which seems to have something to do with the desktop).

I'm now wondering whether it could be a video-card problem. Exactly the same problem occurs on another computer with 16.04 newly upgraded. The only commonality of these computers is that they are both old (7 years) and that the both have Intel Integrated Graphics Controllers. Both are up to date with xserver-xorg-video-intel and the video display works fine on both, but perhaps there is a compatibility/parametrisation problem with gnome-shell ?

Or perhaps the problem is that I do not have Gnome correctly installed? I uninstalled the desktop environment by:
sudo apt-get --purge remove ubuntu-gnome-desktop
and uninstalled Gnome Tweak Tool:
sudo apt-get remove gnome-tweak-tool
sudo apt-get autoremove

Then I installed Gnome Shell and Gnome Tweak Tool:
sudo apt-get install gnome-shell
sudo apt-get install gnome-tweak-tool

After rebooting, gnome-shell is still not running, and I get the same error message with dysfunctional Gnome Tweak Tool.

I am also confused about why the package "gnome-desktop-environment" is not installed along with gnome-shell and why ubuntu-desktop is not installed along with ubuntu-gnome-desktop, when an Ask Ubuntu reply ([https://askubuntu.com/questions/454322/ubuntu-gnome-or-gnome-shell](https://askubuntu.com/questions/454322/ubuntu-gnome-or-gnome-shell)) said that these were the "meta packages" for the two installations. When I try to install "gnome-desktop-environment" with Synaptic it says it can't do before broken packets are repaired, but Synaptic doesn't repair them and trying "sudo apt-get update --fix-missing" and apt-get install -f does not fix anything.

Hoping that you can help, thanks and best regards, John (posting edited at the end since submitted yesterday)

---

### Post by John_Rose on 2017-08-05
I have now solved this problem which was due to a non-evident GNOME intricacy, and not to either a video card incompatibility or to a GNOME installation error. I can launch a functional Gnome Tweak Tool under Ubuntu 14.04 (or on another computer running 16.04 which presented the same problem) by entering "gnome-tweak-tool" in the Alt + F2 command line from any of the desktop flavours (GNOME, Ubuntu, Compiz, Metacity), but NOT from either a normal or a root terminal (which is widely implied on the web to be a valid method)!

---

