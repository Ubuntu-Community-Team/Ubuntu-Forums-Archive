---
title: "LPIA port installation, can't find a mirror"
date: 2008-12-12
forum: General Help
---

### Post by skroops on 2008-12-12
I downloaded the mini.iso and netboot.tar.gz for LPIA architecture from ports.ubuntu.com.  I've gotten the installer to run by PXE and by booting from USB, but when i get to the point to select a mirror, the only option is to enter it manually.

I've tried us.archive.ubuntu.com and ports.ubuntu.com, and a few variations, but nothing is working.  It just hangs at 0% "Downloading release file" for like 20 minutes and then fails.  What is the correct mirror address for the LPIA ubuntu port?

---

### Post by andrewsimpson on 2008-12-12
Hmmm... I had problems with that too.  Can't  remember what I did, but I got around it my brute force.  The correct repository is indeed ports.ubuntu.com in my (working) sources.list.

I done several other lpia installs and it never occurred. Is the repository not always performing?

You might want to look at my previous [post on lpia]("http://ubuntuforums.org/showthread.php?t=1002878") too.

---

