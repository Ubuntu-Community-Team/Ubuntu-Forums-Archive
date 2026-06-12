---
title: "dictionary"
date: 2006-04-28
forum: Desktop Environments
---

### Post by binilbenjamin on 2006-04-28
is there any good offline english dictionary available???

---

### Post by cgjones on 2006-04-28
I'm not at my Ubuntu machine right now, but isn't there some sort of dictionary under the Accessories menu?

---

### Post by binilbenjamin on 2006-04-28
but its an online dictionary...u need to connect to internet to find a words meaning!!i'm looking for an offline dictionary...

---

### Post by cgjones on 2006-04-28
Ah, my bad. I hadn't actually used it before.

---

### Post by usewisdom on 2006-04-28
There is a pretty good thread about [offline dictionaries]("http://ubuntuforums.org/showthread.php?t=131719").

I'm trying out StarDict and find it pretty decent. To install it, go to:
System / Administration / Synaptic Package Manager

Mark for installation: stardict, stardict-common, and optionally stardict-tools

[Download a dictionary tarball]("http://stardict.sourceforge.net/Dictionaries_dictd-www.dict.org.php") or 2 (e.g. Websters or WordNet)

Extract the files from each tarball to a temporary directory (folder).

Start a terminal session (Applications / Accessories / Terminal)

In the terminal, type: sudo nautilus
(this will start nautilus with permission to move files to system directories)

In nautilus, find your temporary directory with the dictionary files, then cut and paste the files to usr/share/stardict/dic
(for each dictionary there will probably be 3 files with names like "dictd_www.dict.org_wn.dict.dz" and "dictd_www.dict.org_wn.dict.ifo" and "dictd_www.dict.org_wn.dict.idx")

StarDict should be ready to run, and you'll find it under Applications / Accessories.

---

### Post by lucia_engel on 2006-04-28
I use Stardict too. I recommend it.

---

