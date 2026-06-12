---
title: "Force apt-get to ignore some packages?"
date: 2009-04-30
forum: General Help
---

### Post by lbelloq on 2009-04-30
Gentlemen:

I've been trying many video plaers, but the one I'm most satisfied with is SMPlayer. I found out that MPlayer's version in Jaunty's official repositories is rather old, and the SMPlayer team recommends to install the MPlayer version they provide in their Launchpad PPA.
The problem is, if I add the PPA repository to my sources.list, and do a "sudo apt-get install smplayer", it still installs the Jaunty's old version, not the PPA's new version.
I read somewhere that I can force apt-get to ignore certain packages from a certain repository; how do I do it?
Thanks in advance,
Léster.

---

### Post by CatKiller on 2009-04-30
Did you update the list of packages after you added the PPA to your sources.list?

sudo apt-get update

should do it.

Otherwise, if for some reason apt-get is **still** selecting the older version, you can use **aptitude**'s forbid-version option.
>        forbid-version
           Forbid a package from being upgraded to a particular version. This
           will prevent aptitude from automatically upgrading to this version,
           but will allow automatic upgrades to future versions. By default,
           aptitude will select the version to which the package would
           normally be upgraded; you may override this selection by appending
           &#8220;=<version>&#8221; to the package name: for instance, &#8220;aptitude
           forbid-version vim=1.2.3.broken-4&#8221;.

           This command is useful for avoiding broken versions of packages
           without having to set and clear manual holds. If you decide you
           really want the forbidden version after all, the &#8220;install&#8221; command
           will remove the ban.


---

