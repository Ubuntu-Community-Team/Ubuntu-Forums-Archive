---
title: "Updating TransmissionBT 1.34 to 1.42"
date: 2009-01-27
forum: General Help
---

### Post by Greg Xix on 2009-01-27
Okay I am at my end here. For almost a week I have been tinkering with this. Transmission is a good program, so maybe I should leave it be as it is. But after I run through all of the commands below nothing seems to change when I reopen the Transmission.


[I]$ tar xvjf transmission-1.42.tar.bz2
$ cd transmission-1.42
$ ./configure -q && make -s
$ su (if necessary for the next line)
$ make instal[/I]l

When I check the version it still says 1.34 (6778)

Sorry for being such a noob.

---

### Post by exploder on 2009-01-27
You need transmission-gtk and transmission-common for Transmission to work. It is easier to grab the packages from here.

[http://www.getdeb.net/search.php?keywords=transmission](http://www.getdeb.net/search.php?keywords=transmission)

This version seems to work fine.

---

### Post by Greg Xix on 2009-01-27
> **exploder said:**
> You need transmission-gtk and transmission-common for Transmission to work. It is easier to grab the packages from here.

[http://www.getdeb.net/search.php?keywords=transmission](http://www.getdeb.net/search.php?keywords=transmission)

This version seems to work fine.


Exploder, I think I owe you some money now. That totally worked! I had to uninstall the old one first(as directed). Then it was a 30 second breeze.

That page needs to be submitted to the **transmissionbt.com** site as a basis for the **MAIN** Primer for upgrading from earlier versions to 1.42

---

### Post by exploder on 2009-01-27
Greg Xix, glad that did the trick!

---

