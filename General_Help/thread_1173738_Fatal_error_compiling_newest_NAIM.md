---
title: "Fatal error compiling newest NAIM"
date: 2009-05-30
forum: General Help
---

### Post by dai_vernon on 2009-05-30
I am attempting to compile the newest version of NAIM.  The version in the repos are one version behind the most recent release.  I need this version because it allows users to appear as mobile, whereas the previous versions do not.  When compiling, I get the following error

./configure
(lots of stuff successfully occurs)
checking for wresize in -lncurses... no
checking for wresize in -lcurses... no
configure: error: unable to find a curses library -- FATAL

Neither of these packages are available in the repos.  Looking around in synaptic and apt-cache search I see a package that appears to be a curses library called libncurses5.  Doing a search and replace in the configure script for lncurses and lcurses and replacing them with libncurses5 does not work.  Is there a library I have access to that will solve this dependency?

Thank you

---

### Post by dai_vernon on 2009-05-31
I have solved the problem.  wresize was contained in libncurses5-dev, which I installed.  The source did not compile cleanly still, but replacing the configure file with an unmodified configure file from the tarball allowed it to do so.

---

