---
title: "Snapshots and a Local Repository"
date: 2006-06-29
forum: Desktop Environments
---

### Post by jsimmons on 2006-06-29
A couple of ideas/questions:

1) Can we take what amounts to a system snapshot backup that could be used to restore a hopelessly hosed up system?  For instance, I've installed Ubuntu, and made sure everything is stable and working okay.  Before I start installing other stuff, I want to take a snapshot of the system so that I can simply restore from the snapshot instead of having to suffer through another 45-minute install session.

2) How about a "local" repository/registry that remembers what we installed on the system (through synaptic of course), where we got it, where the downloaded files are (on our system),  and where it's installed (on our system ).  In the event of a system re-install (or snapshot recovery) this registry could be used recover all previously installed programs (or even electively installed programs with just a few clicks.

**Ubuntu. Usability.  More in common than just the first letter of each word.**

---

### Post by ajgreeny on 2006-06-29
Use partimage to get a copy of the whole partition and you can then restore the image to exactly as it was.  It won't have any of your new docs so you still need to backup regularly.

he local repository you asked for is already there - (/var/cache/apt/archives) unless you've deleted the downloaded files after installation.

---

