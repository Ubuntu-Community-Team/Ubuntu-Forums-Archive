---
title: "Free software in multiverse?"
date: 2006-01-10
forum: General Help
---

### Post by tripleee on 2006-01-10
Where can I find out why a particular package is in multiverse? Or does its being in multiverse simply mean that nobody successfully verified (yet?) that it can't go into universe?

Case in point: the xgobi and ggobi packages are in multiverse, although Debian classifies them as "free" (implicitly, by having them in "main"). Is this a bug, or is there just something I'm overlooking?

---

### Post by tomski on 2006-01-10
the only repository(multiverse,restricted,etc) that is linked to the 'state' of a given package is the backport repository because the packages in there have been 'backported' from dapper

the other repositories names do have a relationship to the packages they contain but only losely 

main = important to the system functionality ie you will need 90% or more from this repo

updates = self explanitory updated packages

security = self explanitory

universe = common packages but not essential for the system

multiverse = not so common not essentiall

some repository hosted outside of the ubuntu community may have packages stored in their repository that you may need a license/serial number to use if they do host these they would normaly be held in a non-free repository

thats about it really hope this info has helped

---

### Post by az on 2006-01-10
[QUOTE=tripleee]Where can I find out why a particular package is in multiverse? Or does its being in multiverse simply mean that nobody successfully verified (yet?) that it can't go into universe?

Case in point: the xgobi and ggobi packages are in multiverse, although Debian classifies them as "free" (implicitly, by having them in "main"). Is this a bug, or is there just something I'm overlooking?[/QUOTE]

  * This release marks the first release under the Common Public License,
    i.e. like its sibbling graphviz, this program has finally been released
    by AT&T/Bell Labs under a license suitable for Debian's main archive! 

Yes, it is a bug.  The package was imported from debian non-free and is now in multiverse.  It will stay in multiverse until someone notices.

Make them notice by filing a bug report in Malone, launchpad's bug-tracker.  

[https://launchpad.net/malone](https://launchpad.net/malone)

---

