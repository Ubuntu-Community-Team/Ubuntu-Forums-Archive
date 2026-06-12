---
title: "Krusader crashes."
date: 2005-07-03
forum: Desktop Environments
---

### Post by quvil on 2005-07-03
Hello everybody.

I installed Krusader 1.60, but some basic manipulations seem to crash it.
For example: I start Krusader and click the following: 

Settings->Configure Krusader->Save settings on exit

That sequence crashes the application. Here is an output I get (all the lines except the last 2 are printed out when Krusader is started):


kbuildsycoca running...
krusader: Initialisising useractions...
QFile::open: No file name specified
krusader: 0 useractions read.
QLayout "unnamed" added to ListPanel "unnamed", which already has a layout
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
QLayout "unnamed" added to ListPanel "unnamed", which already has a layout
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
QLayout "hboxButtons" added to UserMenuAdd "UserMenuAdd", which already has a layout
QLayout "vboxButtons" added to QFrame "page", which already has a layout
KCrash: Application 'krusader' crashing...
Unable to start Dr. Konqi


How it is possible to fix the problem?

---

### Post by sup on 2005-12-03
at least for the thumb creator, install kbioslaves.

---

### Post by ijanos on 2006-01-10
I've found the breezy built of krusader is highly unstable. (Reproductable crashes on 3 breezy machine) So I rebuilt it and crashes gone.
Here's the howto:

Uncomment the deb-src lines in the sources.list and then:
*sudo apt-get -b source kursader*
it will compile the krusader for you and create the .deb file, which you can install with *sudo dpkg -i nameofkrusaderpackge.deb*

PS: It will depend on dpkg-dev and build-essential packages and a few libs which I dont remember (sorry :) ) so if the compile process drop an error just read which lib it need and install the lib*something*-dev package (when you compile something from source, you always need the *-dev packages.)

---

### Post by incrn8 on 2006-02-15
Had the same problem, and after Krusader 1.60 crashed, you couldn't get it to run again. A day or two ago I downloaded the latest 1.70 stable release deb, installed it and have had no problems since then.:D

---

### Post by Sarisar on 2006-06-02
[QUOTE=sup]at least for the thumb creator, install kbioslaves.[/QUOTE]

[QUOTE=The Almighty Google]Your search - kbioslaves - did not match any documents.[/QUOTE]
The almighty Google claims you lie ;)

Actually being serious I'm getting the same problem and searched for kbioslaves, kbio and slave in synaptic and am getting nothing.  So I downloaded the 'sarge' 1.70 deb file and tried to install it.

```
Unpacking krusader (from krusader_1.70.0-0sarge0_i386.deb) ...
dpkg: dependency problems prevent configuration of krusader:
 krusader depends on kdelibs4 (>= 4:3.3.2-6.4); however:
  Package kdelibs4 is not installed.
 krusader depends on libkjsembed1 (>= 4:3.3.2-1); however:
  Package libkjsembed1 is not installed.
 krusader depends on libqt3c102-mt (>= 3:3.3.4); however:
  Package libqt3c102-mt is not installed.
dpkg: error processing krusader (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 krusader
```

OK so a 'sudo apt-get install -f' should fix that (see I'm learning the commands slowly!)

```
The following extra packages will be installed:
  libkjsembed1
The following packages will be REMOVED
  krusader
The following NEW packages will be installed
  libkjsembed1
```

I wasn't reading that it didn't do all the right libs, but there we go (note to self for next time).  So when I tried to install 1.70 again (using dpkg again)

```
 krusader depends on kdelibs4 (>= 4:3.3.2-6.4); however:
  Package kdelibs4 is not installed.
 krusader depends on libqt3c102-mt (>= 3:3.3.4); however:
  Package libqt3c102-mt is not installed.
```

So I try to 'sudo apt-get install kdelibs4' and get told
```
Package kdelibs4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  kdelibs4c2 kdelibs4c2a
E: Package kdelibs4 has no installation candidate
```

OK so lets apt get the c2 one... oh it's replaced by c2a... and that is already installed.

I guess I did it in by upgradding to Dapper over the weekend and that is the problem so I either have to recompile a new version or wait for someone else to do that?  Or am I missing something else?

---

