---
title: "LXDE Ubuntu wireless"
date: 2009-04-30
forum: Desktop Environments
---

### Post by rojodojo on 2009-04-30
Hi,
I just installed LXDE to save some memory on my laptop, but the only thing I can't figure out is how to connect to the internet wirelessly. Unlike, gnome and xfce, it doesn't seem as simple as an icon on the tray.
So how exactly do you connect wireless in LXDE?

---

### Post by kerry_s on 2009-04-30
install "wicd" or "network-manager-gnome"

---

### Post by spillin_dylan on 2009-04-30
Even better yet, you probably already have at least one of them installed (probably network-manager) if you're getting wireless in Gnome & XFCE.  All I think you'll have to do is run either of the above programs to connect.

---

### Post by kerry_s on 2009-04-30
> **spillin_dylan said:**
> Even better yet, you probably already have at least one of them installed (probably network-manager) if you're getting wireless in Gnome & XFCE.  All I think you'll have to do is run either of the above programs to connect.

yeah, if you do have gnome installed, just put "nm-applet &" in your startup.

---

### Post by keithpeter on 2009-05-03
> **kerry_s said:**
> yeah, if you do have gnome installed, just put "nm-applet &" in your startup.

Thanks for this thread. Lxde uses a bit more than half the start up memory that Xubuntu needs (72 vs 130Mb, both with system monitor running).

How do I put nm-applet into my startup so the panel icon appears and lets wifi/ G3 modem networking 'just work'?

Ta

Added Monday: [http://ubuntuforums.org/showthread.php?p=7210414](http://ubuntuforums.org/showthread.php?p=7210414) 
My question has been answered.

---

### Post by deinerson1 on 2010-04-01
I got wireless to work and allowed the user to select a wireless hotspot using these procedures:

Using the menu, open Accessories --> LXTerminal
Open the autostart file for LXDE:

[FONT="Courier New"]sudo nano /etc/xdg/lxsession/LXDE/autostart[/FONT]

Add the following line to enable wireless features for the user:
[FONT="Courier New"]@nm-applet[/FONT]

Save the changes and reboot the system.

The applet will show up in the lower right of the panel. You should be able to select a hotspot and edit connections conveniently henceforth.

---

### Post by spamhog on 2010-05-28
Network-related icons can be VERY CONFUSING in LXDE but I think got the hang of it.

This is on a 10.04 Lucid Lynx default fresh install + LXDE added on:
- the network manager GNOME APPLET icon is one thing
- the network status monitor LXDE PLUGIN is another animal
- but THE ICONS ARE IDENTICAL, a pair of up-down arrows.

To make most changes you can right click on the corresponding item.

NETWORK STATUS MONITOR
On the LXDE "Panel" you can add as many instances of "Network Status Monitor" as you need.
Once they're on, the options of EACH of them allow you to monitor an ethernet or wifi interface.
All monitor interfaces icons have the basic "arrows" icon that blink on traffic.
If an interface is wireless, it also has a non-blinking radio wave symbol on its right.
(I have no Bluetooth, G3 connections to report on).

NETWORK MANAGER APPLET
This is an applet, not a LXDE panel plugin. So to be displayed it needs to be hosted INSIDE a LDXE panel plugin called "System Tray" in the panel preferences. That is on by default, but if the applet does not show, make sure it is.
Its icon is the same pair of up-down arrows but static (no blinking)-
However, if there are no applets running, the "System Tray" has nothing to show, and is empty and practically invisible. If it's turned off, applets may be running but remain invisible.
This applet is not activated in the default install default and it takes a text editor running in sudo mode to add the "@nm-applet" line in the "/etc/xdg/lxsession/LXDE/autostart" file as deinerson1 says. [Thank you! I wasted an hour looking for the correct invocation!].
It can also be started from a terminal as normal user - in which case you'll see a stream of interesting messages as you make it do various things.

It took me quite a while to figure it out. :-(  I keep two NSM's on. I also keep the System Tray with the NMA well away from the NSM's

---

### Post by bradshawd on 2011-05-05
> **deinerson1 said:**
> I got wireless to work and allowed the user to select a wireless hotspot using these procedures:

Using the menu, open Accessories --> LXTerminal
Open the autostart file for LXDE:

[FONT="Courier New"]sudo nano /etc/xdg/lxsession/LXDE/autostart[/FONT]

Add the following line to enable wireless features for the user:
[FONT="Courier New"]@nm-applet[/FONT]

Save the changes and reboot the system.

The applet will show up in the lower right of the panel. You should be able to select a hotspot and edit connections conveniently henceforth.


Thought I would go mad 'til I found this thread.

Many thanks

Derek

---

### Post by Schluter on 2011-07-12
> **kerry_s said:**
> install "wicd" or "network-manager-gnome"


_____________________________



[wireless usb mouse](http://www.wireless9live.com/computer-accessories/wireless-mouses) [wireless keyboards](http://www.wireless9live.com/computer-accessories/wireless-keyboards) [buy wireless router](http://www.wireless9live.com/computer-accessories/wireless-routers)




 All I think you'll have to do is run either of the above programs to connect.

---

### Post by jnorthr on 2011-09-19
> **deinerson1 said:**
> I got wireless to work and allowed the user to select a wireless hotspot using these procedures:

Using the menu, open Accessories --> LXTerminal
Open the autostart file for LXDE:

[FONT="Courier New"]sudo nano /etc/xdg/lxsession/LXDE/autostart[/FONT]

Add the following line to enable wireless features for the user:
[FONT="Courier New"]@nm-applet[/FONT]

Save the changes and reboot the system.

The applet will show up in the lower right of the panel. You should be able to select a hotspot and edit connections conveniently henceforth.

Thanx for this, as I too was facing a bleak future using 11.04 + gnome on a 512MB system.
 
Is there any lighter weight desktop than lxde ? I'm happy with it so far but have no metrics to decide on one, other than a subjective feel.
jimbo

---

### Post by bkratz on 2011-09-19
> **jnorthr said:**
> Thanx for this, as I too was facing a bleak future using 11.04 + gnome on a 512MB system.
 
Is there any lighter weight desktop than lxde ? I'm happy with it so far but have no metrics to decide on one, other than a subjective feel.
jimbo


Here is a very lightweight version based on Ubuntu 10.04. See post #4

[http://ubuntuforums.org/showthread.php?t=1846730](http://ubuntuforums.org/showthread.php?t=1846730)

---

### Post by amjjawad on 2011-09-22
Lubuntu 11.04 has all what I need but YMMV.

---

### Post by HanDez on 2011-12-07
...And for those that don't know..to save changes in LXTerminal you hit Ctrl+X, then it will give you choices, one of which is to hit Y for yes which you must do, then it will present you with the save file which you originally opened, with other options below it...all you simply do is press the Enter key, and it is saved.


BTW... I was one who didn't know...:guitar:...now I am Rockin' !!!

---

### Post by goodhorsehymn on 2011-12-21
> **HanDez said:**
> ...And for those that don't know..to save changes in LXTerminal you hit Ctrl+X, then it will give you choices, one of which is to hit Y for yes which you must do, then it will present you with the save file which you originally opened, with other options below it...all you simply do is press the Enter key, and it is saved.


BTW... I was one who didn't know...:guitar:...now I am Rockin' !!!

You're a legend!  I was clueless here.  Many thanks.

---

### Post by HanDez on 2011-12-25
You are quite welcome!

---

