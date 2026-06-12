---
title: "after update gnome is not working"
date: 2011-04-09
forum: Desktop Environments
---

### Post by chris26jp on 2011-04-09
Hi.
I'm not an expert with Linux so I apologize in advance for my lack of knowledge.  I have Ubuntu 10.04. I had no troubles with gnome until yesterday when I did an auto-update.  I did a shutdown of the computer and the monitor was displaying the purple color inherent in 10.04 Ubuntu.  Weird I thought.  I killed the power.  Later I turned on the computer (desktop) and the log-in screen was fine. Gnome came up, but slow.  The HD light was on and not shutting off.  I clicked an icon and all the icons disappeared.  The HD still constantly on.  I clicked the panel, the menu dropped down for 1 second then the menu vanished.  Further clicks on the panel did nothing.  I was unable to get into another terminal.  I had to hit the reset button.  several attempts later I still have the same problem.  KDE works fine.  Gnome apps in KDE work fine.  I did an update in KDE, seemed a bit better in gnome (meaning it booted up faster) but still the same problem exits.  I have no idea what I broke nor how to fix it.  Can anyone assist?

---

### Post by irv on 2011-04-09
There is a couple of things you can try. First. Restart the computer and in the grub pick the recovery mode. After it boot try to fix broken packages and then restart in normal mode. If this doesn't work try going into the package manager and check to see if you still have any broken packages. If there are any listed delete them. If this doesn't work post back here again.

---

### Post by chris26jp on 2011-04-09
Thank you for the reply.  I rebooted and entered Grub. I selected repair packages. The result was that nothing was broken, nothing removed, nothing installed.  I booted back up (in KDE) and opened syaptic.  I had it look for broken packages. It found nothing.  

I don't know if this is relevant or not, but the GNOME listing in synaptic is unchecked.  But yet I was able to boot into gnome at least a few reboots ago and a few hours ago.  (it just doesn't allow me to do anything in it) Should I tell synaptic to install GNOME again? It said that it would have to remove  gstreamer0.10-gnomevfs if I did.

---

### Post by irv on 2011-04-09
Maybe the next thing to try is re-install gnome desktop. I just notice that gnome-core is not install on my laptop and I am using gnome. What give?
I had a problem the other day with my panel and I had to reload the default panel, Here is the thread that help me with that:  
[http://ubuntuforums.org/showthread.php?t=1721964]("http://ubuntuforums.org/showthread.php?t=1721964")
Maybe give these things a try and see what happens.

---

