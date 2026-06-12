---
title: "chronic dpkg config problems"
date: 2005-03-28
forum: Desktop Environments
---

### Post by koistar on 2005-03-28
Howdy!

   I've managed to install Hoary on my beat up old G3 iBook and i'm trying to work out all the snags..  Whenever i install a new package through synaptic or terminal i get multiple errors.  I chopped up a lil' .gif file which is attached so you can see what happens.  Any ideas very appreciated.  It's been like this since the install.

    Thanks, koistar.

---

### Post by dseomn on 2005-03-28
Keep using the commands ```
sudo apt-get install -f
``` and  ```
sudo dpkg --configure -a
``` until both do nothing, then try again.

---

### Post by statico on 2005-03-28
"Beat up G3," eh? Other than burning through two batteries and the known-faulty DVD-ROM, my little Pismo has been like a rock for four years. It pains me to suggest this:

Have you run any hard drive diagnostic tools? Dunno if the G3's hard drives support it, but it might be worth checking out the 'smartmontools' package which will allow you to query your hard drive S.M.A.R.T. information. It might give you some leads if it appears your drive is failing.

Kind of an out-there thought, but in the past year things you'd never thing as failing have quietly caused me problems: barely bad ram, slightly crappy patch cables, etc.

---

