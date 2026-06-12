---
title: "problems installing gtk headers"
date: 2006-09-21
forum: Desktop Environments
---

### Post by rmillais on 2006-09-21
I cant seem to install any of the GTK2 development headers.  When i try to install libgtk2.0-dev i get a message saying that some packages have unmet dependencies.  I get the following error when trying to install libglib2.0-dev:

```
The following packages have unmet dependencies.
  libglib2.0-dev: Depends: libglib2.0-0 (= 2.10.2-1ubuntu3) but 2.10.3-0ubuntu1 is to be installed

```

The latest version of the headers seems to be behind that of the installed libraries.  I am running a fully up-to-date dapper.  Are the repos simply lagging behind for the dev packages or am i missing something here?  Any help resolving this would be greatly appreciated as there are several pieces of software i would like to compile from source which require the gtk2.0 headers or one the dependent header packages.

---

### Post by rmillais on 2006-09-21
i should mention that i have installed xgl and compiz, and that i have tried commenting out those repositories in my /etc/apt/sources.list file and updating, but get the same errors.

---

### Post by mjziegle on 2006-09-21
I'm having the same problem with libqt3-mt-dev which depends on a lesser version of a library than I already have installed.  I think I'm just going to wait a few days until the repos are updated for the -27 kernel.  If patience doesn't fix the problem I'll force install the old libraries.

---

### Post by rmillais on 2006-09-21
Well i used dpkg --force-version for all the updated gtk2 dependencies missing dev packages and all went fine, except for libpango1.0, which it seems i cant downgrade without uninstalling compiz entirely.  I am reticent about attempting to force-overwrite the libpango with the older (dapper) package, as i dont want to risk breaking anything.  It seems like a major oversight on the part of the compiz packagers not to have included the appropriate dev packages as they did for other newer packages like libxfixes.    I really hope this get fixed in the first release of beryl, otherwise i may have to consider removing xgl + compiz entirely. :(

---

### Post by PabloH on 2006-09-29
See here:

[http://www.ubuntuforums.org/showthread.php?p=1558202#post1558202](http://www.ubuntuforums.org/showthread.php?p=1558202#post1558202)

I am hoping that I am just stupid and am missing something, otherwise I am very unimpresesd with this. It is a very sophmoric mistake. I guess I make a debian VMWare instance to do development work on, as this is really not acceptable. I should not have to force a package or look for it somewhere else just to get the header packages to match their compiled packages in the repository. ARRRRRR. Does ubuntu not have any autobuild dependencies governing their builds? How could they miss/break this on a major release?

---

