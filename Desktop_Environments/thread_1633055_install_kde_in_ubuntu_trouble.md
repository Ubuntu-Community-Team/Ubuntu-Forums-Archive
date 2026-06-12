---
title: "install kde in ubuntu trouble"
date: 2010-11-28
forum: Desktop Environments
---

### Post by stevepoppers on 2010-11-28
I've been googling instructions to install kde to ubuntu. I just want the DE, not the apps, so I've tried kdebase, kde-minimal, kde-core, et cetera. They apparently don't exist? I get either "no installation candidate" or "Unable to locate package."

The hell? Is there a special command for 10.10 or a repository that needs to be added? What can I do?

---

### Post by sikander3786 on 2010-11-28
Those packages are obsolete in Maverick.

[http://ubuntuforums.org/showthread.php?t=1596411](http://ubuntuforums.org/showthread.php?t=1596411)

[http://www.kde.org/download/](http://www.kde.org/download/)

[http://www.ubuntuupdates.org/packages/show/217301](http://www.ubuntuupdates.org/packages/show/217301)

---

### Post by stevepoppers on 2010-11-29
That's kind of befuddling. Have I no choice but to build from source? Is it still possible to get the equivalent of kde-core? Is there no "minimal" sort of kde that I can just slap on top of my running gnome desktop?

---

### Post by ankspo71 on 2010-11-29
Hi,
I think the package you are looking for is now called plasma-desktop.
Hope this helps.

---

### Post by stevepoppers on 2010-11-29
> **ankspo71 said:**
> Hi,
I think the package you are looking for is now called plasma-desktop.
Hope this helps.

Well, it looked good, but I have no option to choose it as my session on login.

---

### Post by ankspo71 on 2010-11-29
hmm, that's odd. Try having a look at kde-plasma-desktop or maybe  kde-standard.

> **kde-plasma-desktop**
the KDE Plasma Desktop and minimal set of applications

KDE is the powerful, integrated, and easy-to-use Free Software desktop platform and suite of applications.

This metapackage pulls in the core modules released with the KDE Software Compilation including the basic KDE Plasma Desktop, minimal set of basic applications (browser, file manager, text editor, system settings, panel, etc.), important libraries and data. 

> **kde-standard**
the KDE Plasma Desktop and standard set of applications

The KDE Software Compilation is the powerful, integrated, and easy-to-use Free Software desktop platform and suite of applications.

This metapackage includes the KDE Plasma Desktop and a selection of the most common used applications in a standard KDE desktop.

---

