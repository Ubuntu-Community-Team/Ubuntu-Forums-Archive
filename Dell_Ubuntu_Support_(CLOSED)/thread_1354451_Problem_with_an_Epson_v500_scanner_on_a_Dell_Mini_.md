---
title: "Problem with an Epson v500 scanner on a Dell Mini 10 with Ubuntu 8.04"
date: 2009-12-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by glendj on 2009-12-13
I downloaded the two driver packages from Avasys -- iscan_2.23.0-3_i386.deb and iscan-plugin-gt-770_2.1.1-2_i386.deb.  



The GDebi Package Installer installed the first package but won't install the 2nd,  I get "Error: Dependency is not satisfiable: iscan.  



 At the same time I successfully added the two packages to an older desktop with hardy and it works great.

I am a  newbie.  Thanks

---

### Post by glendj on 2009-12-14
Hi,

Solved.

The Dell mini has Intel's  low power Intel Architecture (lpia) and doesn't like i386.deb files.

This thread by yakker.yak from Oct. 2008 tells all about it:  [http://ubuntuforums.org/showthread.php?t=962835](http://ubuntuforums.org/showthread.php?t=962835) and also includes a script by feranick that automates the process.

Thanks to all

Glen





                                 [LEFT]package architecture (i386) does not match system (lpia)[/LEFT]
    [LEFT][/LEFT]
    [LEFT][http://ubuntuforums.org/showthread.php?t=962835](http://ubuntuforums.org/showthread.php?t=962835)[/LEFT]

---

