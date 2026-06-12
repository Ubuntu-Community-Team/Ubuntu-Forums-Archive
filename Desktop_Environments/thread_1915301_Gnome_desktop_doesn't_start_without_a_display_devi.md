---
title: "Gnome desktop doesn't start without a display device"
date: 2012-01-25
forum: Desktop Environments
---

### Post by Blue Dude on 2012-01-25
I have a somewhat unorthodox display setup.  I re-purposed an older computer running Ubuntu 10.04 LTS to act as a file server, but since I don't have a spare monitor, and usually don't need one, I have the display output piped through a DVI-to-HDMI connection to an A/V receiver, and then out to my TV.  I usually don't have a keyboard or mouse connected to it, though I can if needed.  Works great, and in the event I need to do anything with the OS, I just use TightVNC to "remote desktop" to the Gnome desktop.  All is well, except...

If I reboot the system remotely, with the A/V receiver turned off (i.e. no EDID info, so apparently no display device connected), the graphical desktop does not start.  The file server does start, and so does the SSH server, so I can command line into the system, but VNC being dependent on Gnome does not.

I think this is a recent problem, and I have changed very little except install the latest image and Kino.  I don't recall having to turn on the receiver first before booting, but I don't try to reboot very often either.  

My question is this: How do I force the system to start up a Gnome session, perhaps with an assumed display device and resolution, without the display device being turned on first?

---

### Post by Blue Dude on 2012-01-26
Let's come at it from a different direction.  Is there a point in the boot process where it's decided whether or not to launch Gnome, or is it always launched?  If it is not launched, how do I do it from the command line?  And if it is already running, how do I get it to restart from the command line with an "assumed" display device or output resolution?  Hopefully I can just adjust a conf file to make sure it launches correctly every time.

I am far from a command line expert, but with command line access (which I already have), that should be more than enough access to determine what's going wrong, right?  I just don't know where to start looking.

---

### Post by Blue Dude on 2012-02-08
This problem occurred with an Radeon card.  I installed an Nvidia card running the closed source driver and this partially fixed the issue.  Now if I don't set up the A/V receiver during boot, Gnome defaults to a 640x480 resolution, which is really low, but it's better than not coming up at all.  I can turn on the receiver and sudo restart gdm to switch to the higher native resolution of the receiver.

It would be very nice to set a resolution on the fly without configuring external hardware like the receiver.  How do you go headless while still keeping a video card installed for occasional use during boot?

---

