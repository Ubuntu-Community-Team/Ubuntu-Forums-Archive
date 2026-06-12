---
title: "Nautilus unable to open certain directories"
date: 2009-04-12
forum: General Help
---

### Post by mcpancakes on 2009-04-12
The issue I am experiencing is this:

In the bottom right corner of the GNOME panel, I had Workspace Switcher and a shortcut to the Trash bin. Today I noticed the Trash missing. I right-clicked on the right-most part of the screen, down there, and up popped the context menu that would have appeared had I right-clicked on a Trash bin icon. So I thought, hm, not good. I tried adding another Trash bin item to the GNOME panel, but that one also was the same sort of 'invisible' (context menu, again, accessible).

Then, I went to Places -> Computer, and up popped a dialogue box telling me that 'Nautilus cannot handle "computer" locations.' I searched a bit and found this thread: [http://ubuntuforums.org/showthread.php?t=801597](http://ubuntuforums.org/showthread.php?t=801597) from May 08. The thread author (and others in there) sound like they're describing an issue similar to mine. They attributed the issue to a bug in an update to 'gvfs'.

So my questions are, 1) is that the likely case for me?, 2) if not what else could it be, 3) if yes, wouldn't others be experiencing this? (are others experiencing this?)

Thanks.

---

### Post by mcpancakes on 2009-04-18
Nevermind, all. Fixed.

<mcpancakes> the problem came from a couple days back, when I was trying install the GTK+ dev files, I didn't know there was a .deb in the repos of it, so I was going wildly from project site to project site, manually making and installing all the different packages that the GTK+ makefile was reporting I needed.
<mcpancakes> they were atk, pango, glibc, and some others (that had no uninstall in the makefile). but anywho I went back just now and did 'make uninstall' on all the ones that could be uninstalled, rebooted, and all issues are gone.
<mcpancakes> of those, I'm thinking the most likely of them to be a problem was glibc.
<mcpancakes> I don't know why making/installing the latest version from the site broke my system in the way that it did, though.

---

### Post by Coimbra on 2009-05-06
Can you help me uninstalling that packages?

I have the same problem.

I've installing atk-1.26.0, glib-2.21.0 and gtk+-2.16.0 doing the makefile and now I don´t know how to remove.

I'm trying to avoid to reinstall ubuntu.

---

### Post by mcpancakes on 2009-05-06
Coimbra: Running "sudo make uninstall" in each package's directory should uninstall the packages. Try restarting, and hopefully the issue will be resolved.

---

