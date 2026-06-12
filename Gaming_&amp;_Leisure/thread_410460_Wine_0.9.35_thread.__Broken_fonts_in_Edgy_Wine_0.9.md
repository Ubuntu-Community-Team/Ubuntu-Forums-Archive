---
title: "Wine 0.9.35 thread.  Broken fonts in Edgy Wine 0.9.35 fixed"
date: 2007-04-15
forum: Gaming &amp; Leisure
---

### Post by YokoZar on 2007-04-15
Sorry folks, the first 0.9.35 packages for Edgy that I uploaded yesterday were broken.  They should be fixed now.  Anyway, this is now the Wine 0.9.35 thread.  

**What's new in this release:**[list][*]Broken aRts sound driver now removed for good.
[*]Many fixes to the Quartz DLL sound support.
[*]File I/O performance improvements.
[*]The usual assortment of Direct3D fixes.
[*]Lots of bug fixes.[/list]

An important feature for this release is the removal of the aRts sound driver. This should once and for all squash the lingering bug that caused winecfg to crash when clicking the audio tab: see [this bug](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/42169) . The reason was broken handling of aRts at the driver level (ie, outside of Wine's control), however hopefully this fix will mean that Wine 0.9.35 will sneak its way into Ubuntu Feisty.


Anyway, let's talk about Wine :)

---

### Post by Kittens on 2007-04-15
Yay I can read Steam again!

---

### Post by stchman on 2007-04-16
> **YokoZar said:**
> Sorry folks, the first 0.9.35 packages for Edgy that I uploaded yesterday were broken.  They should be fixed now.  Anyway, this is now the Wine 0.9.35 thread.  

**What's new in this release:**[list][*]Broken aRts sound driver now removed for good.
[*]Many fixes to the Quartz DLL sound support.
[*]File I/O performance improvements.
[*]The usual assortment of Direct3D fixes.
[*]Lots of bug fixes.[/list]

An important feature for this release is the removal of the aRts sound driver. This should once and for all squash the lingering bug that caused winecfg to crash when clicking the audio tab: see [this bug](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/42169) . The reason was broken handling of aRts at the driver level (ie, outside of Wine's control), however hopefully this fix will mean that Wine 0.9.35 will sneak its way into Ubuntu Feisty.


Anyway, let's talk about Wine :)

Cool, the fonts were all screwed up.  The new version fixed it.

---

### Post by Tanoku on 2007-04-16
Heh, good going.

I reinstalled Steam yesterday and I was like "damnit, Tahoma is installed... I must be doing something wrong!". Nice to see it's fixed now, time for some CSS. :)

---

### Post by frodon on 2007-04-16
Which package are you talking about YokoZar ?

The one from official edgy repo, from edgy backport repo or from edgy winehq  repo ?

---

### Post by AndrewRiedi on 2007-04-16
YokoZar:  I read on wine-devel that you had a problem with libxrender-dev not being installed at build-time.  Can I ask you to also make sure you have libxcursor-dev also installed?  There has been problems with 32-bit cursors for the Guild Wars players in this forum, and 32-bit cursors in wine require Xcursor at the moment.  Thanks.

---

### Post by thom_raindog on 2007-04-16
Yes, that would be awesome. I had just finished installing GW on 0.9.35 and was a bit unhappy to NOT see a cursor :(

---

### Post by SBFC on 2007-04-16
Just a quick question...would it cause problems using winehq's edgy repo in feisty?

---

### Post by YokoZar on 2007-04-16
> **frodon said:**
> Which package are you talking about YokoZar ?

The one from official edgy repo, from edgy backport repo or from edgy winehq  repo ?Edgy winehq v 0.9.35 - it didn't make its way into backports yet as far as I know.

The problem was that libxrender-dev was missing from the build dependencies.

---

### Post by AndrewRiedi on 2007-04-16
> **YokoZar said:**
> Edgy winehq v 0.9.35 - it didn't make its way into backports yet as far as I know.

The problem was that libxrender-dev was missing from the build dependencies.

Did you make sure you have libxcursor-dev also installed before building?  :)

---

### Post by mrazster on 2007-04-17
> **SBFC said:**
> Just a quick question...would it cause problems using winehq's edgy repo in feisty?

It works for me....

---

### Post by YokoZar on 2007-04-17
> **AndrewRiedi said:**
> YokoZar:  I read on wine-devel that you had a problem with libxrender-dev not being installed at build-time.  Can I ask you to also make sure you have libxcursor-dev also installed?  There has been problems with 32-bit cursors for the Guild Wars players in this forum, and 32-bit cursors in wine require Xcursor at the moment.  Thanks.Bah, where are these missing build dependencies coming from...it seemed to be working last version.

Anyway, thanks for this post.  I've created (fixed) Feisty packages and uploaded them.  I've fixed it in Edgy as well (package version -3), and am rebuilding that as I write this.  The 0.9.35 dapper packages (with the same changes) will be up in a few hours.

---

### Post by YokoZar on 2007-04-17
> **AndrewRiedi said:**
> Did you make sure you have libxcursor-dev also installed before building?  :)Well, I did this time.  New edgy packages  are up now :)

---

### Post by AndrewRiedi on 2007-04-17
Thank you.  :)

---

### Post by SBFC on 2007-04-17
> I've created (fixed) Feisty packages and uploaded them.

Thank you very much...been fidgeting while waiting for this. ;)

---

