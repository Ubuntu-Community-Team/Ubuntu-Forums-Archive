---
title: "Adding DVD to Synaptic install source"
date: 2005-12-07
forum: General Help
---

### Post by red devil on 2005-12-07
Hi,
I'm having problems getting Ubuntu 5.10 to accept a DVD as a source for installing new apps.
The DVD is a Linux Format magazine disk - specifically, I want to use it to have Synaptic install Firefox 1.5, but also some other apps.
Ubuntu recognises the DVD - it's mounted on my desktop and I can browse the folders on it.
But when I try to "add CD" in Synaptic to use it as an install source, it's not recognised and I keep getting a "Can't mount CD"-type message... yet it's there, I can see it on my desktop!
What am I doing wrong and how can I fix this?
Thanks all.

---

### Post by brim4brim on 2005-12-07
[QUOTE=red devil]Hi,
I'm having problems getting Ubuntu 5.10 to accept a DVD as a source for installing new apps.
The DVD is a Linux Format magazine disk - specifically, I want to use it to have Synaptic install Firefox 1.5, but also some other apps.
Ubuntu recognises the DVD - it's mounted on my desktop and I can browse the folders on it.
But when I try to "add CD" in Synaptic to use it as an install source, it's not recognised and I keep getting a "Can't mount CD"-type message... yet it's there, I can see it on my desktop!
What am I doing wrong and how can I fix this?
Thanks all.[/QUOTE]

I had problems doing this too, if you play around with the settings in Synaptic you can get it working eventually (but I forget how :???: ), anyway this is something that needs to be made more intuitive in my opinion.  You should be easily able to mount a cd to install packages in Synaptic.

Keep playing with the settings and you should get it working but I found using the apt-get command works a lot better in this situation over the gui.

---

### Post by darknuala on 2005-12-07
Open up a terminal and type:
sudo apt-cdrom add

That should do the trick.

---

### Post by red devil on 2005-12-07
Hi,
Tried the 'sudo apt-cdrom add' but I get a 'Failed to mount CD' error - even though the DVD WAS mounted and it's contents displayed in Nautilus in the background!
The DVD WILL mount, that's not the problem - it's getting Synaptic to access it.
Thanks anyway.

---

