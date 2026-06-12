---
title: "Compiz Problem!"
date: 2009-04-30
forum: Desktop Environments
---

### Post by venomizer on 2009-04-30
Hi all, I'm running the UNR on my MSI Wind and I'm having some problems with Compiz.

I've been trying to install it, and i'm able to mark all packages to install through SPM apart from compizconfig-settings-manager which comes up with this error when I mark it for installation:


> The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.

compizconfig-settings-manager:

Depends: python-compizconfig (>=0.8.2) but it is not installable
I've done a search in SPM for python-compizconfig, but it returns nothing.

I'm a bit of a Linux noob so I might be missing something simple. I think most of the compiz effects have been enabled (are the wobbly windows, automatic snapping to full screen etc. compiz effects? Or are they standard with Ubuntu?), but I can't access the manager to alter their settings (which is presumably what this package is for...)


Thanks

---

### Post by RedSingularity on 2009-04-30
Are you sure you can even run Compiz in the Netbook?  I have a wind as well and i dont think it can support the graphical needs of compiz.  Plus the way the windows are setup in UNR really dont allow for any window related effects.

---

### Post by venomizer on 2009-04-30
Well, some of the effects appear to be enabled. I have gone to System->preferences->Appearance->Visual Effects and have selected 'Extra'

I have wobbly windows, fancy reflective application switched when pressing Super+Tab etc. Are these compiz effects?

---

### Post by RedSingularity on 2009-04-30
They sound like it.  It may be a cut down version for the netbook.  And you have searched "python-compizconfi"?  Have you gone to software sources and made sure "universe" and "multiverse" are checked?

---

### Post by venomizer on 2009-04-30
Maybe.

I've searched python-compizconfig in SPM and I get no results, when I do a sudo apt-get install python-compizconfig I get:

> 
Python-compizconfig is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source.
E: Package python-compizconfig has no installation candidate

Universe and Multiverse are checked in Software Sources

---

### Post by RedSingularity on 2009-04-30
I just did a search for it on my desktop install.  It is a package in the desktop version.  I guess it was removed in the netbook version.

---

### Post by Troyan on 2010-01-12
Hi everyone 

I've just bought an Eee PC, and of course I installed ubuntu (Netbook remix). Once I had the system running I downloaded compiz. then I opened it and I couldn't enable any of its function. So My possible Hipotesis is that this software is not designed to run in this version of ubuntu. But don't be sad, cause I tried the extra effects included in the OS and they worked without troubles :D:D:D 

:D

---

### Post by sqeeek on 2010-07-27
Here's what worked for me, but I wasn't running true Netbook edition, I installed the 'ubuntu netbook-extras' or whatever package, which basically makes it look the same. (I don't know whether or not it ends up actually being the same as normal netbook edition)

Anyway, try going to the Software Center or Synaptic and searching for 'compiz'. Install 'Advanced Desktop Effects Settings (ccsm)'

If you have the desktop effects enabled, and the wobbly windows and stuff works, that's compiz. The above program will allow you to configure it further. 

If that's really not available for the netbook edition, you could try first installing a standard version of 10.04, and then converting it to netbook using the netbook extras package. That should give you all of the functionality of netbook edition, but allow you to use desktop packages. 

Sorry for not being very clear or specific, by the way. I'm new to linux, still working through the learning curve :)

---

### Post by fbobraga on 2010-07-27
there is a simpler tool to manage compiz settings: **simple-ccsm** - I don't know if the dependencies are the same, try it :P

---

