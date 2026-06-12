---
title: "kdeinit error after upgrading to the new kdelibs"
date: 2005-04-23
forum: Desktop Environments
---

### Post by Chunghau on 2005-04-23
Hi guys,

So kdm didn't start today because kdelibs-data failed to install earlier.  So I went about through the command line and "fixed" it.  I did just what you guys said here (before reading the forum, since I didn't have a GUI :p).  I uninstalled knetworkconf, installed kdelibs-data, and then reinstalled knetworkconf.

But I still have the same problem with kdm not starting up.  Here's the most relevant error I could find:

[FONT=Courier New]/usr/bin/kdm_greet: error while loading shared libraries: /usr/lib/libqt-mt.so.3: unexpected reloc type 0x81[/FONT]

If I just do "startx" I get an error from kdeinit about something wrong with my installation, and then quits my kde session.

So I installed ubuntu-desktop and now I'm back in Gnome :)

Please help.  I want to go back to kubuntu's KDE.  Thanks!

---

