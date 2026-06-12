---
title: "Adding applications to xfce taskbar - where are the paths?"
date: 2005-11-08
forum: Desktop Environments
---

### Post by harnadem on 2005-11-08
I am running breezy on an older system and have begun experimenting with the xfce4 desktop.  I want to add my most commonly used applications (eg, Openoffice Writer) to the taskbar.  To do this, I need to know *where* my applications are loctated and their paths.  Is there an easy way to find this out? The applications I am particularly interested in are: Evolution Mail, Openoffice Writer, xmms, and gpodder.  Any help is appreciated.

---

### Post by Ampersand on 2005-11-08
Most programs are in /usr/bin, but you don't generally need the full path when creating launchers. Open office writer is oowriter (or oowriter2 if you're using open office 2), xmms, gpodder and evolution should be the commands for the rest of them.

If you run Synaptic, then look at the properties for programs for which you want to create launchers, it will show the installed files. The files installed in one of the bin folders is the executable.

---

### Post by harnadem on 2005-11-08
[QUOTE=Ampersand]Most programs are in /usr/bin, but you don't generally need the full path when creating launchers. Open office writer is oowriter (or oowriter2 if you're using open office 2), xmms, gpodder and evolution should be the commands for the rest of them.

If you run Synaptic, then look at the properties for programs for which you want to create launchers, it will show the installed files. The files installed in one of the bin folders is the executable.[/QUOTE]


Thank you for the quick and helpful reply!

---

### Post by ranf on 2005-11-08
[QUOTE=Ampersand]Most programs are in /usr/bin, but you don't generally need the full path when creating launchers. Open office writer is oowriter (or oowriter2 if you're using open office 2), xmms, gpodder and evolution should be the commands for the rest of them.[/QUOTE]
Just an additional note: **which <program name>** (run in a terminal) shows the full path to <program name>.

---

### Post by harnadem on 2005-11-09
[QUOTE=ranf]Just an additional note: **which <program name>** (run in a terminal) shows the full path to <program name>.[/QUOTE]

That's what I like about linux - there is always something new to learn.  Thanks for the helpful tip!

---

