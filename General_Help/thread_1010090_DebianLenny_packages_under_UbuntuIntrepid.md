---
title: "Debian/Lenny packages under Ubuntu/Intrepid?"
date: 2008-12-13
forum: General Help
---

### Post by graysky on 2008-12-13
Has anyone ever mixed Debian/Ubuntu packages before?  Is it asking for problems to go mixing the two Distros in my /etc/apt/sources.list ?

For example, I'd like to use the Debian/Lenny kernel under Intrepid to see if it solves my problem with acpi-cpufreq.ko (described [here](http://ubuntuforums.org/showthread.php?t=1000132)).

---

### Post by koenn on 2008-12-13
it's difficult.

by default, apt will look for the newest package in all available repos, so if you have both ubuntu and debian repos enabled, you could have any package replaced by one from the other repo if this happens to have a higher version number any time you run apt-get upgrade.

ubuntu packages are (all ? most of them ?) recompiled with an "ubuntu" version numbering, and dependencies often point to specific versions (usually inside the release). So on top of unpredictable results when doing an upgrade, you'll also have to deal with hard to resolve dependencies.

you can try to manage this with apt-pinning, but it remains to be seen how many ubuntu packages will be willing to work with (or consider their dependensies satiesfied by) a Debian kernel version.

It might be easier to just switch to Debian altogether.

---

### Post by graysky on 2008-12-13
Thanks for the reply.  I'm interested in trying the Lenny kernel to see if that is the cause of my problem with apci.  Guess I can compile my own kernel w/ the lenny settings or something.

---

