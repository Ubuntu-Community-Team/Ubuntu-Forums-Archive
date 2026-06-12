---
title: "Phun Beta 4 on Ubuntu 8.04 Problems"
date: 2008-06-30
forum: Gaming &amp; Leisure
---

### Post by reformer81 on 2008-06-30
I'm trying to get the [Phun Beta 4]("http://phun.cs.umu.se/wiki") working in Ubuntu 8.04 Hardy Heron.  The issue is that it complains about missing libraries.  The first was libglew.  So I followed advice from a site (can't remember which, sorry) that suggested creating a symlink to an older version of the library.  Now I get the following error when running phun:

[INDENT]./phun.bin: error while loading shared libraries: libboost_filesystem.so: cannot open shared object file: No such file or directory[/INDENT]

Does anyone have any clues on how to fix this?

---

### Post by Skootle on 2008-07-01
I have the same problem :S

---

### Post by reformer81 on 2008-07-05
Hmm... been all over the place looking for the solution to this.  No one seems to know.

---

### Post by BenCalot on 2008-07-26
Easy enough. Here we go:

1. Open Synaptic and make sure you have 'libboost-filesystem1.34.1' installed.

2. Open a root file browser and go to '/usr/lib/'.

3. Find 'libboost_filesystem-gcc42-1_34_1.so.1.34.1', right click and 'Make Link'.

4. Rename this link 'libboost_filesystem.so'.

5. Enjoy Phun.

---

