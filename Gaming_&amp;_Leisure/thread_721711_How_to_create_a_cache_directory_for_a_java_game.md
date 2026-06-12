---
title: "How to create a cache directory for a java game?"
date: 2008-03-11
forum: Gaming &amp; Leisure
---

### Post by TaintedBllack on 2008-03-11
When I try to run the game I get the following message:

Error_loader_nocache - Unable to create cache directory.
Runescape was unable to find a suitable place to store its temporary files. To solve this please either:

# Login to your computer as an 'administator' user, and then try loading RuneScape again. This should give it sufficient access to create its temporary cache.

# Or, create a new directory called c:/rscache or /rscache. If possible, set that directory to have full read+write permissions so that all users can write to it. Runescape should then detect that directory and use it for its files.


If some one could tell me how to set up the cache folder I would be very grateful.

---

### Post by Lr5 on 2008-04-25
I ran to that problem after upgrading to 8.04, it turned out icedtea-gcjwebplugin overrode other settings and sun's java wasn't being used. "sudo apt-get remove icedtea-gcjwebplugin" solved the problem for me, no idea if it helps anyone else.

To see which plugin you are using, write "about:plugins" in the Firefox address bar. Icedtea seems not to work with RuneScape.

---

### Post by Primefalcon on 2008-04-25
> **Lr5 said:**
> I run to that problem after upgrading to 8.04, it turned out icedtea-gcjwebplugin overrode other settings and sun's java wasn't being used. "sudo apt-get remove icedtea-gcjwebplugin" solved the problem for me, no idea if it helps anyone else.

To see which plugin you are using, write "about:plugins" in the Firefox address bar. Icedtea seems not to work with RuneScape.

Thx I was having the same problem myself, this fixed it

---

