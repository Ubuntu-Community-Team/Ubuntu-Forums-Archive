---
title: "Removing AWN..."
date: 2007-07-14
forum: Desktop Effects &amp; Customization
---

### Post by Izobalax on 2007-07-14
Hola!

I currently use the SVN-repository version of AWN, but after seeing that I can use a modified version that looks like the Mac OS X Leopard dock, I WANT it.:grin:

However, I fail on the first step. I need to get rid of my current version. I removed it via Synaptic, and removed the repository as well, however I can still see and use AWN. I restarted my system and I can STILL use AWN.

How is this so?

So, how do I COMPLETELY remove AWN?

Ta:grin:

/izo

---

### Post by hyperair on 2007-07-14
Well that's really something. You'll have to post exactly how you installed avant-window-navigator in the first place. This's because you probably compiled it before, then didn't remove it before installing the deb. So the deb just backed up copies of all the files and installed its own copies. When you removed the deb, the original files just got put back.

Also, just make sure you don't have any versions of avant-window-navigator installed from debs anymore.. check the output of this:
```

dpkg --search avant-window-navigator

```

If there's no output then you don't have any awn deb's installed. Otherwise, if you get an output that looks similar to this:
```

hyperair@Hyperair-PC:~$ dpkg --search avant-window-navigator
avant-window-navigator-svn: /usr/share/avant-window-navigator/active
avant-window-navigator-svn: /usr/share/avant-window-navigator/active/glow2.png
avant-window-navigator-svn: /usr/share/avant-window-navigator/active/glow8.png
avant-window-navigator-svn: /usr/share/locale/da/LC_MESSAGES/avant-window-navigator.mo
avant-window-navigator-svn: /usr/share/locale/ru/LC_MESSAGES/avant-window-navigator.mo
avant-window-navigator-svn: /usr/share/locale/de_DE/LC_MESSAGES/avant-window-navigator.mo
avant-window-navigator-svn: /usr/share/locale/it_IT/LC_MESSAGES/avant-window-navigator.mo
....

```
remove the package called "avant-window-navigator-svn" and all other packages listed, as can be seen before the semicolon (:)

---

### Post by Izobalax on 2007-07-14
> **hyperair said:**
> Well that's really something. You'll have to post exactly how you installed avant-window-navigator in the first place. This's because you probably compiled it before, then didn't remove it before installing the deb. So the deb just backed up copies of all the files and installed its own copies. When you removed the deb, the original files just got put back.
I followed the tutorial on these forums: [LINKY](http://ubuntuforums.org/showthread.php?t=385981&highlight=awn)

> **hyperair said:**
> Also, just make sure you don't have any versions of avant-window-navigator installed from debs anymore.. check the output of this:
```

dpkg --search avant-window-navigator

```
Putting this in the terminal gives me this:

```
dpkg: *avant-window-navigator* not found.
```
No debs, apparently, yet I can STILL see and use AWN:(

/izo

---

### Post by hyperair on 2007-07-15
Well, since we have confirmed you have no debs with avant window navigator installed, we can safely use the source uninstaller. First, you must get the avant-window-navigator source code. Extract it, go to the folder you extracted it to, and make sure you can see a Makefile present in that folder.Then open a terminal in that folder (you can install a package called nautilus-open-termianl for a right click option to simplify this) and type:
```

make uninstall

```

That should fix your problem.  Try it =)

---

