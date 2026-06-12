---
title: "HELP! I need somebody...HELP!"
date: 2009-06-05
forum: General Help
---

### Post by maranga6 on 2009-06-05
People,
I'm having a Ubuntu Server, with an NTFS Disk (We Change Windows 2003). I make a backup of my notebook in that Share. The NTFS one.
Well, I have formated my notebook to install Ubuntu Remix and when I was trying to access to the NTFS Drive I apears an error. The fact is that, I can access to any dorectory of the Disk but no to my folder.
I try to put the disk in a Windows Machine and I doesn't recognize it; so I think that the disk is dead. But Ubuntu stills reading some sectors.
The question is; do you know a tool for Scanning the Disk for hardware errors? It must be for NTFS drives instaled in Ubuntu.
Thanks for your help.


Maranga

---

### Post by ddrichardson on 2009-06-05
```
sudo apt-get install ntfsprogs
```
ntfsfix is what you're probably looking for out of that package.

---

### Post by blueridgedog on 2009-06-05
Also, if the partition can't be seen, testdisk may be able to recover it.

You can install it with ```
sudo apt-get install testdisk

```
A howto is here (scroll down):

[http://www.users.bigpond.net.au/hermanzone/p21.html](http://www.users.bigpond.net.au/hermanzone/p21.html)

---

