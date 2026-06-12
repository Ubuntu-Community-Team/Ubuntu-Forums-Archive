---
title: "Missing CompizFusion Plugins on Gutsy Tribe 5"
date: 2007-09-02
forum: Desktop Effects &amp; Customization
---

### Post by EnigMattic on 2007-09-02
So I installed Gutsy (which is undeniably awesome, even at this pre-release stage) and set up Desktop Effects. I made sure I had *compiz-fusion-plugins-extra* and *compiz-fusion-plugins-main* installed.

All seemed well and most of the plugins were working fine, but I seem to be missing a few; in particular I don't seem to have '*Cube Atlantis*' :confused: although I do have '*Cube Gears*'?

Can anyone shed any light on why this might be?

Thanks!

---

### Post by bbmiojo on 2007-09-02
Gutsy has its own packages for Compiz Fusion. 

Atlantis and other plugins only exists in Trevino's repository. What you can do is install these plugins manually.

cheers

---

### Post by Vorian on 2007-09-02
2 things

1 is do not use any 3rd party repo for Gutsy (as they are all packaged for Feisty)
2 The gears, 3d windows, and many other plugins are available in the compiz-fusion-plugins-unofficial package, which is not supported in the Official Ubuntu Repositories for Gutsy.  You will have to compile each extra yourself.

ex:

```
sudo apt-get install git-core
```then
```
mkdir compiz
``` (or whatever you like)
then
```
cd compiz
```then
```
git-clone git://anongit.opencompositing.org/fusion/plugins/3d
```then
```
cd 3d
```then
```
make
```then
```
sudo make install
```or
```
sudo checkinstall
```(this will give you a nice little .deb like the attached)

---

### Post by EnigMattic on 2007-09-03
Thanks Vorian

unfortunately when I try the 'make' command I get this:
```
bcop'ing  : build/3d.xml -> build/3d_options.h/bin/sh: --header=build/3d_options.h: not found
make: *** [build/3d_options.h] Error 127

```

---

### Post by hyperair on 2007-10-06
What are the build dependencies of the 3d plugin? Does anybody know?

---

### Post by chrisccoulson on 2007-10-15
> **EnigMattic said:**
> Thanks Vorian

unfortunately when I try the 'make' command I get this:
```
bcop'ing  : build/3d.xml -> build/3d_options.h/bin/sh: --header=build/3d_options.h: not found
make: *** [build/3d_options.h] Error 127

```
 You need compiz-bcop

Although, even with that installed, the dependencies aren't met in Gutsy. The 3d plugin references compiz-core.h and compiz-cube.h - neither of which exist in compiz-dev.

---

### Post by Ivan Wagner on 2007-10-22
Once I installed using "dpkg" how do I use/select the new plug-ins?

Thank you,

cheers,

Ivan.

---

### Post by Vorian on 2007-10-22
3d is not compatible with the final release of Gutsy.

---

### Post by hyperair on 2007-10-22
Agreed. The build-depends of the 3d plugin are not met. compiz-core.h and compiz-cube.h are missing if I'm not mistaken. So, 3d cannot be built.

---

### Post by Seti on 2007-10-30
> **Vorian said:**
> 3d is not compatible with the final release of Gutsy.


Bummer

---

### Post by hyperair on 2007-10-30
Bummer is right. I'm kind of disappointed at the lack of 3d plugin support as well. Perhaps someone should post a feature request at launchpad or something.

---

### Post by Vorian on 2007-10-31
there are a slew of 'unsupported' plugings included in the compiz-fusion-plugins-unsupported package (3d being one of them) which will not be included because they are _'unsupported'_

---

