---
title: "EEE-PC: Evolution Setup starts when power re-connected"
date: 2009-01-28
forum: General Help
---

### Post by imbjr on 2009-01-28
Like it says in the title:

On my son's EEE-PC, if I disconnect the power and re-connect it, the Evolution setup dialog appears, which is kinda bizarre.

One thing to note: over the weekend the machine suffered the loss of 2Gb of SSD hard-drive space and I had to mark those areas of the disk as unusable before re-installing the system. However, the above is the only odd behaviour I've seen of the PC.

---

### Post by imbjr on 2009-01-28
Well I've checked the acpi scripts and they aren't doing it, not that they should have been in the first place!

A desperate search for any script on the PC that starts evolution is under way.

---

### Post by komputes on 2010-11-09
This bug has been fixed:

[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/268422](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/268422)

---

### Post by imbjr on 2010-11-09
> **komputes said:**
> This bug has been fixed:

[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/268422](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/268422)

Excellent. What a bizarre bug.

---

