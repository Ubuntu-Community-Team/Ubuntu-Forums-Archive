---
title: "Activate eth2 on startup"
date: 2005-12-30
forum: General Help
---

### Post by radicaldreamer on 2005-12-30
For some reason my network card, a wireless cisco does not auto activate on boot, I have written a scipt to start it, but it gets old having to execute the script after each boot so I can use my network card. Is there a way to have it automagically enabled?

---

### Post by darth_vector on 2005-12-30
can you post the content of your /etc/network/interfaces file... you probably need to make some additions to this.

---

### Post by radicaldreamer on 2006-01-04
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth2

# The primary network interface
iface eth2 inet dhcp
wireless-essid Stonewall

auto eth2

---

### Post by radicaldreamer on 2006-01-13
^bump^

Anyone?

---

### Post by radicaldreamer on 2006-01-26
I'm suprised that NOONE knows the answer to this. Its simple things like this that are keeping linux where it is.

---

### Post by Adrian on 2006-01-26
[QUOTE=radicaldreamer]For some reason my network card, a wireless cisco does not auto activate on boot, I have written a scipt to start it, but it gets old having to execute the script after each boot so I can use my network card. Is there a way to have it automagically enabled?[/QUOTE]

Try putting the script in **/etc/init.d** and make a *symlink* to it in **/etc/rc3.d** and **/etc/rc5.d** (these are the run levels you normally want).

Don't forget to make it executable.

---

