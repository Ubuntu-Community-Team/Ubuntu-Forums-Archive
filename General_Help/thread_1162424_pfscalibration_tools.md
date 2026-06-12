---
title: "pfscalibration tools"
date: 2009-05-17
forum: General Help
---

### Post by brunogirin on 2009-05-17
The Ubuntu repositories include the pfstools and pfstmo packages that provide the [pfstools]("http://pfstools.sourceforge.net/") HDR and tone mapping utilities. However, there seems to be no package for the [pfscalibration]("http://pfstools.sourceforge.net/pfscalibration.html") tools, such as [pfshdrcalibrate]("http://pfstools.sourceforge.net/man1/pfshdrcalibrate.1.html"). Are they in a different package or should I build them from source code? If the latter, what is the correct procedure for requesting they be added to the Ubuntu repositories: file a bug in Launchpad?

---

### Post by j.daniel on 2009-12-03
**Hi,**

  The only option right now AFAIK is to download the source from sourceforge and compile yourself.

  Note: I spent two days trying to find where in *$%& the pfscalibration package were (compiling pfstools myself etc) before I found - more of an accident than not - that pfscalibration is packaged in its own little tarball.

  On the pfstools project page, instead of pressing the "Download now" button, choose "View all files" and there - in the bottom of that list - you will find the pfscalibration tarball.

  [I have heard]("http://ubuntuforums.org/showthread.php?t=1272527") that libpfs-dev is required to successfully compile this, so ensure that you have it installed beforehand.

Cheers!
/ Daniel

---

