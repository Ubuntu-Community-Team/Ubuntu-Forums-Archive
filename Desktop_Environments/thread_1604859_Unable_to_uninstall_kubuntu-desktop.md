---
title: "Unable to uninstall kubuntu-desktop?"
date: 2010-10-24
forum: Desktop Environments
---

### Post by DemonSharkKisame on 2010-10-24
Although I do enjoy KDE, I've decided to remove it so as to free up space from my machine, as well as resolve an issue with Dolphin constantly presenting itself as the default file manager in GNOME. However, when I try to apt-get remove the desktop and its packages in terminal, I get this: 
"[FONT=Lucida Console]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openoffice.org-kde is not installed, so not removed
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:[/FONT] [FONT=Lucida Console]
 openjdk-6-jre : Depends: libgif4 (>= 4.1.4) but it is not going to be installed
                 Recommends: ttf-dejavu-extra but it is not going to be installed
E: Broken packages[/FONT]"

Is this a bug specific to 10.10 or am I missing something somewhere? Installing package openoffice.org-kde seems to result in the same problem.

---

