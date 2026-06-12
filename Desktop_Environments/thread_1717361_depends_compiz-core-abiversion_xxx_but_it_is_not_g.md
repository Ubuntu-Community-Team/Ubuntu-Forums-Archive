---
title: "depends compiz-core-abiversion xxx but it is not going to be installed :utouch-compiz"
date: 2011-03-29
forum: Desktop Environments
---

### Post by jaxxed on 2011-03-29
THIS IS A BIT OF AN EARLY ADOPTION, BUT I HAVE HAD THIS ISSUE BEFORE, AND WAS UNABLE TO RESOLVE IT.

I have installed an up-to-date Natty ubuntu installation.  I've enabled all of the standard repos, plus all of the update repos (including backports.)  I have not enabled any PPAs as of yet.

I'm trying to take a look at the current state of the utouch implentation, but I can't get it to work.  I have some packages installed, but have no configuration tools, and no multitouch.

I noticed that the compiz-utouch package isn't installed, so I tried to install it but I get an apt dependency violation:

<code>
Depends: compiz-core-abiversion-20110126 but it is not going to be installed
</code>

Does this mean that the utouch-compiz package needs a newer version of compiz-core?  if so how do I match the abi-version to a oackage version?  Do I need a PPA or an additional repository?

---

### Post by dr_james2k on 2011-05-19
If anyone has managed to find a fix for this I would greatly appreciate it.

I suspect installing the required version of compiz from source might be the way to go but I'd hope there would be a more straightforward fix.

UPDATE:  Ok, using the utouch PPA does sort the problem, but beware - its a bit unstable.

---

