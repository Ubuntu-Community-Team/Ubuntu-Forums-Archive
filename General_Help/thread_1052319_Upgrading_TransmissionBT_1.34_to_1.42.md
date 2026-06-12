---
title: "Upgrading TransmissionBT 1.34 to 1.42"
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

### Post by sdennie on 2009-01-27
Moved to general help.

My guess is the version you are compiling is installing in /usr/local and not /usr so, you are still seeing the older version.  You could uninstall the older version and see if that helps or, better, you could uninstall your new version and instead use getdeb to get the newest version of transimission: [http://www.getdeb.net/app/Transmission](http://www.getdeb.net/app/Transmission)

---

