---
title: "Cannot install any packages anymore!"
date: 2009-02-15
forum: General Help
---

### Post by The MAX on 2009-02-15
Everything worked fine when I used 32 bit but now that I have 8.10 64 bit installed if I try to DL any packages using ```
sudo apt-get install
``` it spits this out

```
hughie@The-Flash:~$ sudo apt-get install gparted
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing blender (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_intrepid-updates_universe_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

```

Any ideas why its doing this? It is not letting me install any packages, I've restarted my x-server but it is still not letting me.
If anyone here has an Idea I'd appreciate it.

---

### Post by mcduck on 2009-02-15
What happens when you run "sudo apt-get update"? Any errors?

---

### Post by The MAX on 2009-02-15
hmm that seems to have done the trick.

ran that, and now i'm able to install packages.

Thank you.

---

