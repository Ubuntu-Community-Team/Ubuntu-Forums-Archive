---
title: "Ubuntu : 64-bit packages making sure"
date: 2009-04-05
forum: General Help
---

### Post by AnthonyNYU on 2009-04-05
Newbie here, building my first Linux system. Going to use Ubuntu Intrepid (8.10). I am interested in having the following "stuff" on my system:

gcc 4.x.x 
GAP
Octave
CUDA SDK
COIN-OR
Ajunta 
Kdevelop
TeXnicCenter
MikTeX

I want to confirm that Ubuntu has binaries for: gcc 4.x.x, GAP, Octave, Kdevelop, and  Ajunta. I am double checking here! And that the command: sudo apt-get install XXXXX, is what will begin an install.

Thanks,

_System_
mob Intel DX58SO extreme 
cpu Intel Core i7 920  
gpu EVGA NVIDIA GTX 260 core 216, two of the them 
RAM Corsair Dominator 2GB RAM stix, three of them 6 GB total 

Currently using Windows Vista 64 bit. I would like to move onto something more serious and mature.

---

### Post by whelanh on 2009-04-05
I currently have a dual boot system with 64 bit Windows Vista (hardly ever use) and 64 bit Kubuntu Jaunty beta.  So while I am not using Intrepid, I can say for Jaunty that most of what you are looking for is readily available.  Specifically, gcc version 4.3.3 is my "default" gcc.  Kdevelop is available. The Octave version available using apt-get is Octave 3.0.  If you run "aptitude search xxxxx", you can see what packages are available (or search in synaptic in Ubuntu).  "aptitude show xxxx" gives you a description.  So "aptitude show gap" gives:

hugh@Desktop:~$ aptitude show gap
Package: gap                     
State: not installed
Version: 4r4p10-2
Priority: optional
Section: universe/math
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 81.9k
Depends: gap-core, gap-libs, gap-online-help
Recommends: gap-dev, gap-doc, gap-prim-groups, gap-small-groups, gap-trans-groups
Suggests: gap-character-tables, gap-small-groups-extra, gap-table-of-marks
Description: Groups, Algorithms and Programming computer algebra system
 GAP is a system for computational discrete algebra with particular emphasis on
 computational group theory, but which has already proved useful also in other areas.   In
 the example text, gap is used to analyse Rubik's Cube using group theory.  A kernel
 implements a Pascal-like language.

 This is a dummy package that depends on the standard GAP components.

 Homepage: <http://www.gap-system.org/>

I didn't see Ajunta in my apt-get database, but it seems like it would be installable from [http://www.anjuta.org/downloads](http://www.anjuta.org/downloads)  (there are no shortage of nice IDE's including Kdevelop, Eclipse, QtCreator etc.).

Finally I generally use "aptitude install --with-recommends xxxxxx" instead of apt-get (will install other recommended packages with package you want to install).  Finally the command "apt-get build-dep xxxxxx" can be handy if you want to compile sources yourself for a package...it will install the libraries necessary to build package xxxxx.

Best,
Hugh

---

### Post by measekite on 2009-04-06
> **whelanh said:**
> I currently have a dual boot system with 64 bit Windows Vista (hardly ever use) and 64 bit Kubuntu Jaunty beta.  So while I am not using Intrepid, I can say for Jaunty that most of what you are looking for is readily available.  Specifically, gcc version 4.3.3 is my "default" gcc.  Kdevelop is available. The Octave version available using apt-get is Octave 3.0.  If you run "aptitude search xxxxx", you can see what packages are available (or search in synaptic in Ubuntu).  "aptitude show xxxx" gives you a description.  So "aptitude show gap" gives:

hugh@Desktop:~$ aptitude show gap
Package: gap                     
State: not installed
Version: 4r4p10-2
Priority: optional
Section: universe/math
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 81.9k
Depends: gap-core, gap-libs, gap-online-help
Recommends: gap-dev, gap-doc, gap-prim-groups, gap-small-groups, gap-trans-groups
Suggests: gap-character-tables, gap-small-groups-extra, gap-table-of-marks
Description: Groups, Algorithms and Programming computer algebra system
 GAP is a system for computational discrete algebra with particular emphasis on
 computational group theory, but which has already proved useful also in other areas.   In
 the example text, gap is used to analyse Rubik's Cube using group theory.  A kernel
 implements a Pascal-like language.

 This is a dummy package that depends on the standard GAP components.

 Homepage: <http://www.gap-system.org/>

I didn't see Ajunta in my apt-get database, but it seems like it would be installable from [http://www.anjuta.org/downloads](http://www.anjuta.org/downloads)  (there are no shortage of nice IDE's including Kdevelop, Eclipse, QtCreator etc.).

Finally I generally use "aptitude install --with-recommends xxxxxx" instead of apt-get (will install other recommended packages with package you want to install).  Finally the command "apt-get build-dep xxxxxx" can be handy if you want to compile sources yourself for a package...it will install the libraries necessary to build package xxxxx.

Best,
Hugh
I thought 64 bit OS can run both 64 and 32 bit so why would there be an issue?

---

### Post by mb_webguy on 2009-04-06
> **measekite said:**
> I thought 64 bit OS can run both 64 and 32 bit so why would there be an issue?

Yes, if you have a 32-bit deb you can force the architecture to install it on a 64-bit system.  But it will run as a 32-bit application, and not take advantage of the greater computing power of the 64-bit system.  If the source is available, you can compile the software for the 64-bit system.

Basically, the only software you have to worry about not being available for a 64-bit system is closed-source software for which a 64-bit version isn't available.  This is an essentially moot issue, since most major software developers now provide 64-bit versions of their software, and it's not an issue at all with open-source software.

---

