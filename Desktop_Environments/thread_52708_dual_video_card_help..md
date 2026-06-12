---
title: "dual video card help."
date: 2005-07-28
forum: Desktop Environments
---

### Post by wparsons on 2005-07-28
I'm having a bit of trouble setting up my dual displays, and was hoping someone could lend a hand.

I have an AGP Radeon AIW, and a PCI VooDoo3.  The Radeon is set as the primary device in the BIOS, yet when I boot Ubuntu it displays anything related to the xserver on the VooDoo3.

I had this machine setup to use both with Debian linux before, and had to manually edit the xfree86 configuration, but I haven't been able to find everything in Ubuntu.

Both cards are displayed in the device listing, but I couldn't see anywhere to easily configure it to use both cards.

Any help would be awesome!

---

### Post by Sam on 2005-07-28
Maybe [this howto](http://ubuntuforums.org/showthread.php?t=31686) can help you...

---

### Post by wparsons on 2005-07-28
That howto is exactly what I was looking for!  I was looking for an xfree86 config file, not an xorg.conf.

Only issue now, terrible resolution on the VooDoo3 card... It should be able to handle more than 640x480@24 bits shouldn't it?

In my xorg.conf file I took out all the resolutions under 800x600 on both cards, and yet I still get the VooDoo3 using 640x480...

---

