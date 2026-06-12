---
title: "Window title problem"
date: 2009-01-31
forum: General Help
---

### Post by gsxruk on 2009-01-31
Hi,

I just upgraded to 8.10 yesterday from 8.04 (fresh install).  I notice that each window title bar is not stable.  Often the bar will be half white (or maybe transparent) and the other half orange as usual.

Anybody have any ideas why this is?

Thanks.

---

### Post by zakany on 2009-01-31
Don't know *why*, but I think we have [a work-around]("http://ubuntuforums.org/showthread.php?t=1053591") at least.

---

### Post by gsxruk on 2009-01-31
Thought it would end up an nVidia problem.  I'll wait to see if a newer driver fixes the problem in the future.

Thanks for your help.

---

### Post by zakany on 2009-02-02
> **gsxruk said:**
> Thought it would end up an nVidia problem.  I'll wait to see if a newer driver fixes the problem in the future.

It may be an Nvidia glitch, but there's something different with the Human theme since it doesn't occur with the others.

---

### Post by gsxruk on 2009-02-02
Just tried that and you're right, the problem disappears with a different theme.  Do you know if this has/should this be reported as a bug?  If it has do you know what it is filed under. I'd like to keep a track on the progress of it.

Thanks.

---

### Post by gsxruk on 2009-02-02
Found it here [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/186382](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/186382)

---

### Post by gsxruk on 2009-02-05
I have received an answer on this from bug 186382 which involved installing a new package in Synaptic package manager.  I have installed driver version 180 and everything seems fine.

Before doing this the driver I had activated was listed in "Hardware Drivers" but this new one is not.  Can somebody please explain the difference between the original 177 driver and the 180 driver and how the installation differs?

Thanks.

---

