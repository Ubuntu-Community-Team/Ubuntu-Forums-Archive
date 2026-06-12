---
title: "[SOLVED] Compiz working good, updates just kill the the thing...."
date: 2008-04-15
forum: Desktop Effects &amp; Customization
---

### Post by hurinth on 2008-04-15
[B][COLOR="Olive"]Help please, I am using gusty freshly installed without any updates from the update manager.
I was using compiz fusion just fine (well, some bug making it crash from time to time and leaving it off), so everything was just fine, then I run the update manager hoping the abundant updates for compiz packages would solve the bug... But surprise..... After rebooting my machine it loaded a dialog box saying that I had to choose Safe Graphics mode. downgraded the resolution to VGA with no desktop effects obviously. Also my keyboard layout changed

PLEASE HELP

What should be done in this situations? 

Asus Crosshair mobo
Asus VW2220 22" LCD
EVGA 8800 gts
Kingston Hyperx Memory
AMD 5600 X2 Dual Core

I will certainly THANK who ever provides me with a solution. Thanks again[/COLOR][/B]

---

### Post by pastalavista on 2008-04-15
Have you tried going to system > administration > hardware drivers and enable all proprietary drivers? If so and it still doesn't work you might have to update the drivers or find compatible linux display drivers

---

### Post by hurinth on 2008-04-15
[B][COLOR="Olive"]Yeah man this is the second time the updates screw up everything. Last time I went and enabled again the drivers but still nothing changed. Only got 800x600 resolution and no effects.

Let me say again that I was working just fine even with the updates BEFORE I rebooted. Thus, I had the drivers enabled for my nVIDIA card

Is there some command  I could run to put all things in order?[/COLOR][/B]

---

### Post by pastalavista on 2008-04-15
I looked around when I had some problems with compiz and found several helps here:

[http://ubuntuforums.org/showthread.php?t=622084&highlight=configure+hardware](http://ubuntuforums.org/showthread.php?t=622084&highlight=configure+hardware)

good luck

---

### Post by rune0077 on 2008-04-15
I would suggest using Synaptic to reinstall the restricted drivers (or, if you used Envy, remove the drivers and then install them again with Envy). Then do a restart and see if that fixes thing.

EDIT: after restarting, if you still get low-graphic mode, you may have to set Desktop Effects to Customize in System > Preferences > Appearance, see if it'll let you.

---

### Post by hurinth on 2008-04-15
[B][COLOR="Olive"]K I will reinstall the drivers as soon as I get home. The weird thing is, that without the drivers, just after the fresh install, Ubuntu gave me 1440xwhatever the other # is right away. NO drivers needed. Right now Im lucky to get 800x600!

In the meantime I will read the link pastalavista gave me

I'll let you guys know[/COLOR][/B]

---

### Post by Zorael on 2008-04-15
If it still doesn't work, we would like to see the contents of your **/etc/X11/xorg.conf** and your **/var/log/Xorg.0.log** files. Just open them in Gedit and paste the contents here. :>

---

### Post by hurinth on 2008-04-16
[B][COLOR="Olive"]Rune you got it

The drivers were missconfigured or damaged or who knows what after updating linux. I just uninstalled and reinstall and everything went the Alberto Millone way.

Zorael, what is that about KDE in your signature anyway?[/COLOR][/B]

---

### Post by Zorael on 2008-04-16
Merely opinion.

I find KDE to be vastly more user-friendly and easy to use when compared to Gnome. It is underappreciated and most don't try it. After they've read articles about Ubuntu, most new linux users never try the alternative 'buntus - of which Kubuntu is the biggest contender, I'd wager. They "default" to Ubuntu.

[There have been reports and benchmarks](http://ktown.kde.org/~seli/memory/desktop_benchmark.html) about how KDE even take up less memory than Gnome does, even though Kubuntu feels more fleshed-out as a desktop environment. To admit, I was sort of surprised Ubuntu wasn't based on KDE to begin with, with an alternative Gubuntu for the die-hard Gnomelings. If you want light-weight, I recommend Xfce (Xubuntu).

If you've tried both KDE and Gnome (Kubuntu and Ubuntu, or via some other distro), and you still prefer Gnome, then you rock - g0game.

If you've never seen KDE, I'd suggest you download and burn a copy of the Kubuntu Live CD and see if it suits your tastes.

---

### Post by hurinth on 2008-04-17
[COLOR="Olive"]**Ok. Interesting perspective Zorael. Right now I have opens Suse with KDE just to take a look at Yast, networking and KDE of course. We'll see how it goes.**[/COLOR]

---

