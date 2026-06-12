---
title: "updating a (python-based) package in intrepid"
date: 2009-02-12
forum: General Help
---

### Post by listener on 2009-02-12
Hi.  I've been using pytags and pytagsfs which are command-line programs for tagging audio files and working with them, for quite a while.   It is coded in Python.  What I cannot figure out about it is this:  I have two computers each with Intrepid, one has the 'proposed' and 'backports' repos enabled, the other does not.  I also have the PPA enabled for this package.  The most recent version is something like 1.0.9.0 and on this machine is 1.0.8.0 - these are the versions which the package manager softwares indicate are currently installed.  Yet, on both machines, an earlier version (0.6.0) is what is actually being invoked.  This is evidenced both by the --version argument, and the pytags syntax, which has changed.

I have researched and tried some different things with dpkg, update-python-modules, etc.  I do not understand why some indicators are that the recent versions are installed, while I am only able to run the much earlier version.  Can anyone help me with this, please?

The source for both versions seems to be on the machines, in two different places?

Thanks!

---

