---
title: "xserver-xorg-core and linux-image-686"
date: 2006-08-23
forum: Desktop Environments
---

### Post by DigitalDuality on 2006-08-23
ok, well before seeing it on digg.com, i accidentally upgraded the bunk Ubuntu update for xserver-xorg-core and just figured i'd wait until another update came out before i restarted.

Days have passed and i've forgotten all about it and i read an article that selecting linux-image-686 in synaptic could probably get better performance out of my processor.

So that's what i did and .. i rebooted.

It wouldn't load my nvidia card no matter what i did.  It has taken me reverting back to linux-image-386, and getting rid of my nvidia card and running off the on-board card, as well as reverting back to the old xserver-xorg-core just to get things running again.

now mind you i didn't go changing too much, just a bunch of sudo apt-get install and sudo apt-get remove.  That's it.

Yet i'm still unable (even with /etc/X11/xorg.conf configured properly and drivers for nvidia removed and reinstalled) to get this system working with my nvidia card.  It keeps saying the kernel module for it won't load.

Any suggestions?

---

### Post by az on 2006-08-23
You should have been advised to install linux-686 instead of linux-image-686.

The former installs the corresponding linux-restricted-modules for you (along witht the linux-image-686 packages).  The latter only installs the linux-image.

sudo apt-get install linux-686

---

