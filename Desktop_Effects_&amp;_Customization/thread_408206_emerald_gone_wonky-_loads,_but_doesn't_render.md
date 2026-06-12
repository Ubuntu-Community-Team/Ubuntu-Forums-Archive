---
title: "emerald gone wonky- loads, but doesn't render"
date: 2007-04-13
forum: Desktop Effects &amp; Customization
---

### Post by d3athp3nguin on 2007-04-13
I recently installed Beryl-SVN, and found it to be a bit... twitchy.  It liked to crash.  So, I uninstalled it and any associated packages (emerald, etc) and reinstalled version 2 from the official ubuntu repositories.


Now, when I try to load beryl, the window decorator Emerald acts wonky.  The themes from emerald technically load, but they only display a sliver of the decorator theme on the top-left corner of each window.  In other words, the decorator themes are 99.9% invisible- the buttons work, but you can't see them.  When I change emerald themes, the sliver that I can see changes accordingly.

I tried disabling decorator transparency in Beryl Settings and in Emerald's settings, but no dice.

I don't know if this matters, but I checked the versions of beryl-manager, emerald, and beryl core: beryl-manager is 0.2, emerald is 0.2, but beryl-core is .3-svn???  This smells fishy...

Any ideas?

---

### Post by d3athp3nguin on 2007-04-13
Once again I am a master at answering my own questions.

I figured out that not all of the beryl and emerald packages were being uninstalled properly, resulting in half of my packages being SVN and half being 0.2.0.  After manually hunting down and removing every infernal package that had anything to do with beryl and emerald, and manually deleting profile/setting info they left behind, it works like a charm.

Sorry to clog the forums.

---

### Post by Kalior on 2007-07-19
can you elaborate a little on what you did to fix this? I'm having the same problem

---

### Post by bdtgp on 2007-07-19
Maybe you should try compiz fusion instead.  It's more stable and has all the features of Beryl.  Plus you can still use Emerald themes.

---

