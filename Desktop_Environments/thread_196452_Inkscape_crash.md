---
title: "Inkscape crash"
date: 2006-06-14
forum: Desktop Environments
---

### Post by blueshome on 2006-06-14
I've a problem whit inskape,
the same explaned in this thread
[http://www.ubuntuforums.org/showthread.php?t=184422]("http://www.ubuntuforums.org/showthread.php?t=184422")

Someone has a idea how to solve it
without install the unstable (0.44) version from source

Thanks in advance to all

P.S.
I tried to work whith sodipodi
but also this program crash in the same way

---

### Post by blueshome on 2006-06-14
Up Up

---

### Post by sigge on 2006-08-25
> **blueshome said:**
> 
P.S.
I tried to work whith sodipodi
but also this program crash in the same way

And with the exact same function!

How weird is that? I'm not a programmer, but doesn't that point to some kind of shared library with a bug or something?

---

### Post by Wijsneus on 2006-09-19
I have the same problem, but only after yesterday when i last updated and got a new kernel.

i'd love to upgrade to the 0.44 (or whatever the latest release is) but i'm to lazy to find out how ;)

---

### Post by lamego on 2006-09-19
You can get the latest version (0.44.1) for Dapper at getdeb:

[http://www.getdeb.net/search.php?keywords=inkscape](http://www.getdeb.net/search.php?keywords=inkscape)

---

### Post by rocknrolf77 on 2006-09-20
> **lamego said:**
> You can get the latest version (0.44.1) for Dapper at getdeb:

[http://www.getdeb.net/search.php?keywords=inkscape](http://www.getdeb.net/search.php?keywords=inkscape)

Getdeb would make a good link from the forum. Are you involved in the project? Just found it a couple of hours ago. Finally got brasero up and running. Good to have the latest packages that easy. Very nice burn software. Has to be the fastest out there with that many options. :)

---

### Post by Wijsneus on 2006-09-22
> **lamego said:**
> You can get the latest version (0.44.1) for Dapper at getdeb:

[http://www.getdeb.net/search.php?keywords=inkscape](http://www.getdeb.net/search.php?keywords=inkscape)

ow man - thanx - that totaly saves my ***; :D

---

### Post by finferflu on 2006-09-23
Uh, good!

I was actually looking for the latest version of Inkscape, pefect!

Thanks a lot! :D

---

### Post by lamego on 2006-09-23
rocknrolf77,
I am the getdeb creator, I am still working on the page, like the applications categories, how to run, etc. Only later I will try some public announcments :)

---

### Post by JeevesBond on 2006-09-24
It would be good if you had a proper repository going. One that we can just point apt to via /etc/apt/sources.list and it would 'just work'. :)

Surely it would be better (for the community) if you contributed to the [backports project](https://launchpad.net/products/dapper-backports) instead of going off on your own?


*** EDIT ***
Ahem, well as it turns out there might be a need for what you're doing. They [won't backport the latest version of F-Spot](https://launchpad.net/products/dapper-backports/+bug/61417). You don't have a deb for that... Yet.

Am getting miffed with having to wait for software, maybe switching to Debian and enabling the test repos would be even better than trusting random people to package things. :-|

---

### Post by alvonsius on 2006-09-24
Hi there rocknrolf77, nice place you got there ... This is what I'm lookin for huehuehue ...

---

### Post by lamego on 2006-09-24
JeevesBond,
has have been experienced lately, repository upgrades are very sensitive, getdeb is for people needing sepcific upgrades, not for people which doesn't care to get their system unusable.

F-Spot depends on neweer mono libs which are not included on Dapper, the getdeb policy does not include upgrading core libraries (to make sure you don't mess the standard versions).

> Am getting miffed with having to wait for software, maybe switching to Debian and enabling the test repos would be even better than trusting random people to package things. 
If you are looking for testing why don't you go for Edgy ?

---

