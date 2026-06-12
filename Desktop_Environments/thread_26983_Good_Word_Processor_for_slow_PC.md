---
title: "Good Word Processor for slow PC"
date: 2005-04-14
forum: Desktop Environments
---

### Post by Chris_Durham on 2005-04-14
I'm running Ubuntu and OpenOffice.Org on a 500Mhz PII laptop without a whole lot of memory. Everything but OpenOffice runs fine. It's not that OpenOffice doesn't run well, it's just so large that it takes forever to open. My primary need is word processing and I need to be able to export .doc files and would like to be able to output .odt's because I'll probably move back to OpenOffice when I get a better laptop. Any suggestions? Thanks

---

### Post by Stormy Eyes on 2005-04-14
[QUOTE=Chris_Durham]I'm running Ubuntu and OpenOffice.Org on a 500Mhz PII laptop without a whole lot of memory. Everything but OpenOffice runs fine. It's not that OpenOffice doesn't run well, it's just so large that it takes forever to open. My primary need is word processing and I need to be able to export .doc files and would like to be able to output .odt's because I'll probably move back to OpenOffice when I get a better laptop. Any suggestions? Thanks[/QUOTE]

Try Abiword.

---

### Post by p!=f on 2005-04-14
I've found AbiWord really fast..
```

[~] > wajig show abiword-gnome
Package: abiword-gnome
Priority: optional
Section: gnome
Installed-Size: 6700
Maintainer: Masayuki Hatta (mhatta) <mhatta@debian.org>
Architecture: i386
Source: abiword
Version: 2.2.2-1ubuntu2
Replaces: abiword-common (<< 2.0.14-1), abiword
Depends: [cut]
Conflicts: abiword
Filename: pool/main/a/abiword/abiword-gnome_2.2.2-1ubuntu2_i386.deb
Size: 2305298
MD5sum: b2f3db5ecfd74c02faf5836e7f72e301
Description: WYSIWYG word processor based on GTK2/GNOME2
 AbiWord is the first application of a complete, open source office
 suite. The upstream source includes cross-platform support for Win32,
 BeOS, and QNX as well as GTK+ on Unix.
 .
 This package contains the AbiWord binary built with GTK2/GNOME2.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```
Note that AbiWord is part of gnome-office package
```

Depends: gnome-core (= 62ubuntu2), abiword-gnome (>= 2.0.14), dia-gnome, gimp (>= 2.0.6), gnumeric (>= 1.3.93), planner, inkscape | sodipodi
Recommends: gnucash

```

---

### Post by Chris_Durham on 2005-04-14
Thanks. I'll give it a go.

---

### Post by Stormy Eyes on 2005-04-14
[QUOTE=Chris_Durham]Thanks. I'll give it a go.[/QUOTE]

Good luck. I should mention that I've had trouble with Abiword 2.0's styles (even after RTFM I couldn't get the damned thing to format paragraphs and headings the way I wanted it to), which pushed me towards OpenOffice.org in the first place. Hoary's got 2.2, so your may have a different experience.

---

### Post by Chris_Durham on 2005-04-14
Just got it installed and it opens lighnting fast comapred to OpenOffice, so I'll work with it for a couple of days and see how it goes. My only complaint is that it doesn't open OpenOffice 2 text docu (.odt) so I'll need to convert the ones I have to an earlier version, but luckily I've only got a handful of them. I guess it makes sense since OpenOffice 2 is just in Beta at this point. Anyway, thanks for the advice.

---

### Post by ntd on 2005-04-14
You can also try prelinking OpenOffice...it'll speed up load times (sometimes by a lot, cut it in half at least for me)

I believe an 
apt-get install ooprelink

will do the trick, but I am not at home so can't check for sure to make sure that that is the right name for the package...it might have another o in the name

---

### Post by Stormy Eyes on 2005-04-14
[QUOTE=Chris_Durham]My only complaint is that it doesn't open OpenOffice 2 text docu (.odt) so I'll need to convert the ones I have to an earlier version, but luckily I've only got a handful of them. I guess it makes sense since OpenOffice 2 is just in Beta at this point. Anyway, thanks for the advice.[/QUOTE]

If you really want OpenOffice.org 2, you can use the new Breezy Badger repositories and do the following: **sudo apt-get install openoffice.org2 openoffice.org2-gnome**. I'm using it now to work on my novel, though I'm sticking with the *.sxw format until OpenOffice.org 2 is officially released and widely adopted. :)

PS: I did a dist-upgrade to Breezy and everything looks creamy so far.

---

### Post by Casey on 2005-04-15
[QUOTE=Stormy Eyes]If you really want OpenOffice.org 2, you can use the new Breezy Badger repositories and do the following: **sudo apt-get install openoffice.org2 openoffice.org2-gnome**. I'm using it now to work on my novel, though I'm sticking with the *.sxw format until OpenOffice.org 2 is officially released and widely adopted. :)

PS: I did a dist-upgrade to Breezy and everything looks creamy so far.[/QUOTE]

OpenOffice2 is also in Hoary (if someone doesn't want to risk the Breezy upgrade).  It's not part of the default desktop however, but it can be installed via synaptic.  I have not felt that OO2 is any faster than OO1.X so I'm not sure if it would fit the needs of a faster-opening word processor.

---

### Post by Stormy Eyes on 2005-04-15
[QUOTE=Casey]OpenOffice2 is also in Hoary (if someone doesn't want to risk the Breezy upgrade).  It's not part of the default desktop however, but it can be installed via synaptic.  I have not felt that OO2 is any faster than OO1.X so I'm not sure if it would fit the needs of a faster-opening word processor.[/QUOTE]

I tried installing OpenOffice.org2 from hoary universe and got 404 errors when trying to retrieve packages. Installing from breezy worked. I also did a dist-upgrade for chuckles, and my machine's still purring.

---

