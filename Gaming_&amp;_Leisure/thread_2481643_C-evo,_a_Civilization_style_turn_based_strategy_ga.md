---
title: "C-evo, a Civilization style turn based strategy game"
date: 2022-12-05
forum: Gaming &amp; Leisure
---

### Post by ueter on 2022-12-05
C-evo has been ported to Linux.
[https://en.wikipedia.org/wiki/C-evo](https://en.wikipedia.org/wiki/C-evo)
[https://civilization.fandom.com/wiki/C-evo](https://civilization.fandom.com/wiki/C-evo)

Its from the Civ 2 era, but not just a clone. 
Very real differences from Civ2 (and Freeciv)
[https://civilization.fandom.com/wiki/C-evo/Divergences_from_Civilization_II](https://civilization.fandom.com/wiki/C-evo/Divergences_from_Civilization_II)


I've created my own fork of it here
[https://sourceforge.net/projects/c-evo-eh/](https://sourceforge.net/projects/c-evo-eh/)

The main new features, are larger map sizes
and extra translations of the in-game manual.
French, Spanish & Portuguese added.

Prebuilt binaries for Ubuntu can be obtained from the OBS
[https://build.opensuse.org/package/show/home/peterBBB/c-evo]("https://build.opensuse.org/package/show/home:PeterBBB/c-evo")


Cheers,
Peter

---

### Post by lacrosby on 2023-02-02
Interesting, I'll need to take a poke.

---

### Post by ueter on 2023-04-08
It's now an official package starting with Lubnar Lobster
[URL="https://launchpad.net/ubuntu/+source/c-evo-dh"]https://launchpad.net/ubuntu/+source/c-evo-dh


[/URL] Also I've now released an external Map Generator tool, for more interesting & hostile worlds.
[https://sourceforge.net/projects/cevomapgen](https://sourceforge.net/projects/cevomapgen)
[URL="https://software.opensuse.org//download.html?project=home%3APeterBBB&package=cevomapgen"]https://software.opensuse.org//download.html?project=home%3APeterBBB&package=cevomapgen

[/URL] Cheers, 
Peter

---

### Post by webaake on 2023-04-08
How do you compile this on Linux? I got the source code but couldn't find any compile instructions.

---

### Post by ueter on 2023-04-08
I've uploaded the debian tarball now. that should make things easier!
Just unpack the debian tarball into the cevomapgen-25 folder.
I usually use debuild from devscripts to build.

You will need Lazarus & FPC installed.

Hope this helps,
Peter

---

### Post by webaake on 2023-04-08
Thanks!  I'll give it  a go.!

---

