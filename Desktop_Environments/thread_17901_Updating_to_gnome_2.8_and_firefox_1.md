---
title: "Updating to gnome 2.8 and firefox 1"
date: 2005-03-03
forum: Desktop Environments
---

### Post by joplass on 2005-03-03
How do I update to gnome 2.8 and firefox 1.0 or later?  Do I use “apt-get install gnome 2.8” for example?

---

### Post by bored2k on 2005-03-03
[QUOTE=joplass]How do I update to gnome 2.8 and firefox 1.0 or later?  Do I use “apt-get install gnome 2.8” for example?[/QUOTE]


For the Firefox 1.0 backport add this to ur repository 
> ## Backport sources - Ubuntu Warty
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) warty-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) warty-extras main universe multiverse restricted 

just upgrade or apt-get install mozilla-firefox [all ur preferences/tabs/ext/ stay so dont worry]

i did a fresh install on warty 4.10 and i hav gnome 2.8.1

---

### Post by joplass on 2005-03-03
For my Warty I believe it’s the latest one because I downloaded it last Saturday from here [http://ubuntu.mirrors.tds.net/releases/warty/](http://ubuntu.mirrors.tds.net/releases/warty/).  So I will assume that it’s 4.10 with gnome 2.8.1.  Am I wrong?  As of mozilla-firefox, I will add those two links in there.  Although I am not sure about what you mean by "backport-sources", I could only think that it's synaptic we are talking about.
As always thank you for your help.

---

### Post by joplass on 2005-03-03
bored2k
I got this after I added those two links to the repository.  I copy and pasted them as you posted them:

"Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

ttp://backports.ubuntuforums.org/backports/dists/warty/warty-backports/binary-i386/Packages.gz: 404 Not Found
[http://backports.ubuntuforums.org/backports/dists/warty/main/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/warty/main/binary-i386/Packages.gz:) 404 Not Found
[http://backports.ubuntuforums.org/backports/dists/warty/universe/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/warty/universe/binary-i386/Packages.gz:) 404 Not Found
[http://backports.ubuntuforums.org/backports/dists/warty/multiverse/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/warty/multiverse/binary-i386/Packages.gz:) 404 Not Found
[http://backports.ubuntuforums.org/backports/dists/warty/restricted/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/warty/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://backports.ubuntuforums.org/backports/dists/warty/warty-extras/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/warty/warty-extras/binary-i386/Packages.gz:) 404 Not Found
[http://backports.ubuntuforums.org/backports/dists/warty/main/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/warty/main/binary-i386/Packages.gz:) 404 Not Found
[http://backports.ubuntuforums.org/backports/dists/warty/universe/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/warty/universe/binary-i386/Packages.gz:) 404 Not Found
[http://backports.ubuntuforums.org/backports/dists/warty/multiverse/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/warty/multiverse/binary-i386/Packages.gz:) 404 Not Found
[http://backports.ubuntuforums.org/backports/dists/warty/restricted/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/warty/restricted/binary-i386/Packages.gz:) 404 Not Found"

---

### Post by bored2k on 2005-03-03
I just did apt-get update , this is proof that those repos are still O.K.

> Get:11 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) warty-backports/restricted Packages [20B]
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable/main Release
Get:12 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) warty-backports/restricted Release [99B]
Get:13 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) warty-extras/main Packages [20B]
Get:14 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) warty-extras/main Release [90B]
Get:15 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) warty-extras/universe Packages [2388B]
Get:16 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) warty-extras/universe Release [94B]
Get:17 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) warty-extras/multiverse Packages [20B]
Get:18 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) warty-extras/multiverse Release [96B]
Get:19 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) warty-extras/restricted Packages [20B]
Get:20 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) warty-extras/restricted Release [96B]
Fetched 46.4kB in 8s (5344B/s)
Reading Package Lists... Done 

I dunno how t.h. u added them, but heres the normal way :
sudo gedit /etc/apt/sources.list

append > deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) warty-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) warty-extras main universe multiverse restricted 

[Ubuntu BACKPORTS](http://backports.ubuntuforums.org/) 

apt-get update

---

### Post by joplass on 2005-03-04
Thanks!  Worked like a charm!

---

