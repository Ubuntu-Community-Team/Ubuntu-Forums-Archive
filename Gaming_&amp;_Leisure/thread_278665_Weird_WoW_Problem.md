---
title: "Weird WoW Problem"
date: 2006-10-16
forum: Gaming &amp; Leisure
---

### Post by Emceay on 2006-10-16
Okay.. I installed ubuntu fresh, then i installed wine following the instructions from the ubuntu documentation [here.]("https://help.ubuntu.com/community/WorldofWarcraft") After using winecfg to configure it for OSS, the terminal displays a brief message, then the installer opens. 
> fixme:font:CreateScalableFontResourceW (1,0xbc6108,0xbc2208,(nil)): stub
However when I click the install button the license agreement is blank, and then a blank error message pops up. 

Has anyone gotten this kind of error before? Anyone have an idea of how to fix it? I was sure it would work this time on a fresh install...

---

### Post by hikaricore on 2006-10-17
The license agreement is often blank or garbled, unless you use another variation of wine such as cedega or cxoffice that have a work around for this.  The WoW setup is kinda quirky, I've had random errors popup and such every other time I try reinstall it.  I've even had to run wine as root (sudo) before to get WoW to let me install into a drive I have write access to originally.  *slaps forehead*

Anyways as usual make sure you have a recent version of wine installed, 0.9.22 is current and I can install fine with this version.  Also wine doesn't always need to be patched anymore unless you have specific hardware that requires a patch, see: [http://appdb.winehq.org/appview.php?iVersionId=5606](http://appdb.winehq.org/appview.php?iVersionId=5606)

One last thought, if you're trying to install from the CDs, copy them to a hard drive and try the install from there, CD access in certain windows based installers (namely wow) is very quirky.

Good luck and sorry I couldn't be more help.

---

