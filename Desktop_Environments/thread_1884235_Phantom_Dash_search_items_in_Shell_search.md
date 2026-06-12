---
title: "Phantom Dash search items in Shell search"
date: 2011-11-20
forum: Desktop Environments
---

### Post by Copper Bezel on 2011-11-20
Folks,

Am I the only one getting phantom search entries for deleted items in the Dash search under Shell? 

Steps to replicate:

Create a text file with a unique name from gedit. (Say, pickles.txt.)

Search for it from the Dash, and it appears as expected.

Delete the file, and restart Shell. Search again.

The file still appears, but of course can't be loaded. Moving a file, then, will create two entries. Yuck.

It's not a Zeitgeist problem, because I don't see the same behavior in Synapse at all. Files are removed from the search index the moment they're deleted. It could be residual crap from some extension I've tried and disabled or removed, but I want to be sure. If this is universal, it's a bug.

---

### Post by Morgen on 2011-12-05
This bug has been reported here: [https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/892997](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/892997)

Unfortunately I can't find a fix or workaround.

---

