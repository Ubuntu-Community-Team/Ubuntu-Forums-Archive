---
title: "search in yelp"
date: 2006-08-07
forum: Desktop Environments
---

### Post by aferrandi on 2006-08-07
I upgraded from version 5.10 to 6.06 a pair of weeks ago.
The only thing that does not work well is yelp: when I search for a word (for example 'acpi') I always get 0 results.
Beagle has been installed already in version 5.10, so I suppose the problem is in the configuration of yelp or beagle.
In beagle-settings I can see that only my home directory is indexed. I tried to add other directories (usr/shared/man for example) but nothing happened.
Does someone know what I have to do to let it work?

---

### Post by aferrandi on 2006-08-18
Does someone have an example of the correct beagle configuration (beagle-settings)?

---

### Post by lolo2908 on 2006-08-29
Same problem for me. Can't find any solutions yet. Still searching on google and different community forums.

---

### Post by lolo2908 on 2006-09-01
Have found two solutions tested on an Archlinux box (sorry, I use both, but more often Archlinux for flexibility reasons).

If Yelp is built with the configuration option --with-search=basic, it uses "classic" tools to search inside documentation pages. Espacially, it uses scrollkeeper to perform search inside application documents registered  with ScrollKeeper. And, what even more interesting, with whatis. But first, the whatis database has to be built with the command : sudo LANGUAGE=en(or whatever) makewhatis -w. 

If Yelp is built with the configuration option --with-search=beagle, you have to build the documentation database with beagle. This is provided by the beagle-crawl-system script (in the beagle package). You have to tweak '/etc/beagle/crawl-documentation' so that manpages are indexed. But, personnaly, I had more meaningful results with the first solution (despite it appears to sometimes buggy).

Well, hope this helps. I struggle to find an acceptable solution as Yelp documentation and forums lack information about Yelp internals.

---

