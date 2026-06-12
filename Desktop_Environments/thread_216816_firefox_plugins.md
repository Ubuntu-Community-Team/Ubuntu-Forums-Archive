---
title: "firefox plugins"
date: 2006-07-16
forum: Desktop Environments
---

### Post by charbo on 2006-07-16
Hi,

I added the Universe and Multiverse, and ran apt-get update.

Still, 

apt-get install flashplugin-nonfree 

and 

apt-get install sun-java5-plugin

fail with error saying that those packages could not be found.

Does anybody know if these packages are not provided anymore?

Going through the forum, it seems like people were installing these files at least until several days ago.

I look forward to finding out.

Thank you!

---

### Post by adam.tropics on 2006-07-16
No, they are still there,

[]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=flashplugin-nonfree&searchon=name&subword=1&version=all&release=all")
[sun-java5-plugin]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=sun-java5-plugin&searchon=name&subword=1&version=all&release=all")

Quite apart from that though, you would want to be doing the apt-get, with sudo apt-get. And just to be safe, check the sources.list again, it can't hurt!

---

### Post by carontis on 2006-07-16
For what concerning sun-java5-plugin you can find it in Synaptic; for the flash plugin, well I had it installed in automatic from a website (I don't remember where)...
Hope this helps you a little...

bye

---

### Post by charbo on 2006-07-16
It seems that I had not actually made the universe and multiverse available.:oops: 

All I made available was backport universe and multiverse.
Once I included the universe and multiverse to the regular repository part also, it found flashplugin-nonfree.

Sorry, and Thank you for your help.

---

### Post by charbo on 2006-07-16
adam.tropics,

you were right.
double checking the sources.list solved this problem.

Thank you.

---

### Post by adam.tropics on 2006-07-16
You're welcome

---

