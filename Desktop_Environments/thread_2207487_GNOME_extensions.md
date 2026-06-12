---
title: "GNOME extensions"
date: 2014-02-23
forum: Desktop Environments
---

### Post by Da_Panther on 2014-02-23
Hey everyone,

I've been running the new version of gnome (I believe GNOME 3.8?) for a while now... since it came out. 

Is there any intention for the various extensions programmers to bring 3.8 compatibility to their extensions? Over half of my extensions are outdated since the upgrade. 

Thanks!

---

### Post by buzzingrobot on 2014-02-24
The extensions are unofficial efforts from individual contributors, other than a few that the Gnome team has "adopted" to support the classic look.  So, it's up to each extension writer to update.

Sometimes -- emphasis on *sometimes* -- an extension can be made to work with a newer Gnome Shell release if the version number included in its metadata.json filed is increased.  Each installed extension will be located in a folder in ~/.local/share/gnome-shell/extensions. (And often /usr/share/gnome-shell/extensions.)  Inside each extension sub-directory is a "metadata.json" file.  Open it in a text editor and locate something that looks like this:```

"shell-version": [
    "3.8", 
    "3.10"
  ], 


```

Add an entry that corresponds to your specific Gnome version, save the file, restart Gnome Shell or log out and in, and, if you're lucky, the extension may work.

This will not work if the extension's code needs to be revised to accommodate the new Gnome release, of course, or if it depends on some functionality that's been altered or removed.

Your current Gnome version is displayed in "System Setting->Details".

Finally, I've found that sometimes simply reinstalling an extension after a Gnome update will do the trick.

---

