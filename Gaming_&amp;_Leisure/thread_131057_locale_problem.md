---
title: "locale problem"
date: 2006-02-15
forum: Gaming &amp; Leisure
---

### Post by soonindallas on 2006-02-15
I was running TC:E tonight !!not as root!! but it would appear that my locale settings got messed up.

The TC:E interface is now only available to me in French.  An uninstall and reinstall of the game did not restore the english language interface I started with.

In the terminal I see this:

```
Verifying archive integrity... All good.
Uncompressing True Combat: Elite 0.48-english Installer...............................................................
Searching Return to Castle Wolfenstein: Enemy Territory....
Return to Castle Wolfenstein: Enemy Territory found in /usr/local/games/enemy-territory
Installing in /usr/local/games/enemy-territory
Done.

Gdk-WARNING **: locale not supported by C library
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_FR:en",
        LC_ALL = (unset),
        LANG = "en_US"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
ET 2.60 linux-i386 Mar 10 2005
```

the language "en_FR:en" makes no sense to me.

how can I restore this to the initial state ? (prolly was UK english)

---

### Post by soonindallas on 2006-02-16
ok.  this is resolved after looking at the truecombat.com forums.  maybe it was a locale problem and maybe it wasn't, but the origin is some pk3 files the server placed in my profile folder.

the offending pk3 have filenames that commence with "zzzz_" and you just need to delete them from your et profile folder.  this is not the game install folder, it's the .etwolf folder in your home.

---

