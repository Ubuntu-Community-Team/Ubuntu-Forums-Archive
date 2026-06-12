---
title: "Where is File Lock Version"
date: 2005-07-27
forum: Desktop Environments
---

### Post by Irony on 2005-07-27
I've successfully installed mplayer-586 (the Pentium version, though my computer is an Athlon 3500). It works fine. I did it via synaptic.

However I saw some instructions saying that I can do a File>Lock version on mplayer in synaptic; apparently this stops it being accidently updated. I can't see this in synaptic, would someone point it out, thanks.

---

### Post by Mr Frosti on 2005-07-27
To lock the version of an application, do the following steps:

1. Go to "System" -> "Administration" -> "Synaptic Package Manager"

2. Type in your password

3. Search for "mplayer-586" (or anything else you want to lock)

4. Select the package, and then click "Package" -> "Lock Version"

It will now remain the same, regardless of if there is a new release available.

I locked the version of my kernel, and header files to 6.10.5-686-smp to keep my multi-processor support, even when Ubuntu updates its default kernel.

---

### Post by Irony on 2005-07-27
Thanks for that - its now got a padlock sign on it.

---

