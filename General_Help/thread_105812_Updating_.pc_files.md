---
title: "Updating .pc files"
date: 2005-12-19
forum: General Help
---

### Post by Snoopy2052 on 2005-12-19
I've just installed Ubuntu, and am loving it so far. It just feels... cleaner, and I love the interplay between the GUI and the CLI.

However, whenever I try to use **./configure** while installing anything (so far anything from a tarball -- it's been AbiWord and a couple of things including Danger from the Deep off the latest Linux Format coverdisc), there's always been an issue with not finding the .pc file for some package or other (usually glib2.0). So, I tried hunting for them all with **sudo slocate "*.pc"** after updating the locate database with **updatedb**, and found just 10. Nine of them were in /usr/lib/pkgconfig and none of the 9 of them there look anything like what I want.
(for reference, they're gnome-doc-utils, gnome-media-profiles, gnome-mime-data-2.0, gnome-system-tools, gst-python-0.8, pyorbit-2, rhythmbox, shared-mime-info and xml2po)

So what's going on? Do I not actually need any other .pc files? And if not, what goes on with **./configure** when it tries to find them? Is there any way to update the .pc files in any way? 

Oh, and it keeps suggesting that I update the PKG_CONFIG_PATH environment variable to let it know where the missing .pc files are. If it does come down to the .pc files being somewhere other, how does one update an environment variable, anyway? 

Cheers in advance,
Snoopy2052

---

### Post by Snoopy2052 on 2005-12-19
Oh, it's worth noting that I don't have a net connection from my home PC. Yet. I'm hoping to get broadband in the new year.

---

### Post by bjourne on 2005-12-28
.pc-files are used by the program pkg-config to determine which compiler flags and paths to use when compiling packages using installed packages. I believe the reason you are not finding them is because you haven't installed the necessary -dev packages. Debian has two versions of library packages - one for only linking with the library and another, -dev-package, for developing with it. You need to install libglib2.0-dev, libgtk2.0-dev and probably some more.

---

