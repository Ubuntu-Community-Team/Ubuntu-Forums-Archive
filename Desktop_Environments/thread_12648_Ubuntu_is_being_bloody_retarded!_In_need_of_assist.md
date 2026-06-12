---
title: "Ubuntu is being bloody retarded! In need of assistence w/ regard to Printing."
date: 2005-01-26
forum: Desktop Environments
---

### Post by black hole sun on 2005-01-26
I'm trying to install my printer, which works on *every other distrobution known to man*; this inlcudes slackware, linux from scratch, gentoo, mandrake, fedora. Why won't it work on ubuntu? Well, I'll tell you why...because the engineer's of this distro had this absolutely fantastically **BRILLIANT** idea of disabling the CUPS web interface so that installing the lexmark driver is damn near impossible. Now, I'm no noob; I follow this guide;

[http://gentoo-wiki.com/HOWTO_Lexmark_Printers](http://gentoo-wiki.com/HOWTO_Lexmark_Printers)

Of course, it's for gentoo, but it works with everything else with minor modification (I should know, as I WROTE that guide's initial version and maintain it to this day). Well anyways, for some reason following the above procedue nets me nothing, because the *gnome interface wont see my printer driver*! My model # isn't listed and so the driver is inaccessible... How can I make it see the light? I've tried the "install driver" dialog and directed it manually to the pdd, but then it just inanely tells me "This is already installed" :| Help, I'm lost under an avalanche of needless gui. :mad: 




Sigh...sorry if this comes off as flamebait, but I was pretty angry when i wrote it (heck im still angry), but now more frustrated than anything.

---

### Post by Cygnia on 2005-01-26
Have you tried installing the cups-gimp-print drivers in Synaptic? After that your printer may show in the list of models to choose from.

---

### Post by black hole sun on 2005-01-26
[QUOTE=Cygnia]Have you tried installing the cups-gimp-print drivers in Synaptic? After that your printer may show in the list of models to choose from.[/QUOTE]
So very close. It showed up, even the version number, but alas, the driver on the driver list did not. :-& There was just "Standard" ?? Let me play around for a little bit...

ARGH, no luck. is there any way to get around this silly gnome problem, like, a command or something??

---

### Post by Pluk on 2005-01-26
> Administration over the web interface is disabled by default since it
requires the CUPS daemon to be able to read /etc/shadow. If you want to
enable web administration with shadow passwords (authentication type
'basic'), put the user cupsys into group shadow by

adduser cupsys shadow

as root.

this info is in /usr/share/doc/cupsys/README.Debian.gz

---

