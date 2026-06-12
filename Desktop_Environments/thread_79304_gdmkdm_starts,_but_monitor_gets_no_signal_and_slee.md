---
title: "gdm/kdm starts, but monitor gets no signal and sleeps"
date: 2005-10-19
forum: Desktop Environments
---

### Post by BROKEN_LADDER on 2005-10-19
when i "upgraded" to breezy, i initially had this problem where the gdm/kdm would start (i could hear it) but the monitor would go to sleep with no signal.  i could only get to gdm/kdm from recovery mode by running it from root command line.

eventually, with some dpkg-reconfigure xserver-xorg and other poking around, i got it to boot up to the gdm.  however, once i'm in a session and i either try to exit back to gdm, or initiate a new x session on another screen, i get the same problem.  instant monitor loss, to "no signal".  again, i can hear the gdm start sound, but my monitor "dies".  this is unrecoverable.  no ctrl-alt-backspace or anything changes the problem.  it just makes the monitor spark back to life for a quick second, and then back to sleep.  occasionally, when heading to this abyss, i see an entire screen of white momentarily.  i have loaded my old backup xorg.conf, poked around at the current xorg.conf, and rerun dkpg-reconfigure, but to no avail.

---

