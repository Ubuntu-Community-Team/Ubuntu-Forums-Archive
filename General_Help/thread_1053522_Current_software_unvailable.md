---
title: "Current software unvailable?"
date: 2009-01-28
forum: General Help
---

### Post by -ovid- on 2009-01-28
Hi All, 

Firstly, thanks for being such an active forum - I've already used many of the posts to help me.

I've recently migrated from Gentoo to Ubuntu and although I really appreciate the ease of setup of the hardware I do have a problem accessing current and up-to-date software packages.

Maybe I'm missing the Ubuntu terminology but it's not jumping out at me so some help would be greatly appreciated.

My issue is directly this, for example:
Kernel
*- 2.6.28r2 - highest available non-beta in other distro trees
*- 2.6.27r11 - highest available by default in Intrepid

Nmap
*- 4.75 - highest available non-beta from Insecure.org and other distro trees
*- 4.62 - highest available by default in Intrepid

Some other applications and packages are also in a similar state. =\

Package management is very important so compiling my own kernel and apps can be done of course - however keeping track of package changes and dependencies  is what package management is all about so that's not an option I want to consider for longer term systems/solutions. This is not a scalable option.

Am i missing something glaringly obvious? =( 
What do I need to change in order to use current software that is default in a few other package management trees?

Do I need to change to the Jaunty tree? Does that mean I'm not able to follow more up-to-date packages under Intrepid?
What do I have to do to unhide/unmask the "unstable" versions under Intrepid?

Thanks in advance for your pointers and advice!

---

### Post by mb_webguy on 2009-01-28
Ubuntu has a stepped release schedule, unlike some other distributions that have rolling releases.  Other than security updates, packages are "locked in" for each release.  This helps ensure a more stable system, since all of the packages can be tested against a fixed package set, rather than one that continuously changes.

The downside is that in order to get new releases of software through the official repos, you have to upgrade to the new version when one is released.  Otherwise, you have to add third-party repositories, install software from debs, or compile it yourself.  There are quite a few software sources targeted at providing more recent versions of applications for Ubuntu, including GetDeb and many PPAs.  Newer versions of applications are occasionally backported to older versions of Ubuntu from the newer versions, and can be found in the backports repository.

---

### Post by -ovid- on 2009-02-05
Thanks for clarifying this mb_webguy - much appreciated.

I've gone with Jaunty for now for the short term whilst I assess my options and Jaunty gives me access to what I need for now...

Thanks again!

---

