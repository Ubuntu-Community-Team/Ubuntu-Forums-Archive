---
title: "/usr/local/share/frozen-bubble/ missing"
date: 2007-03-21
forum: Gaming &amp; Leisure
---

### Post by elreteipos on 2007-03-21
I installed frozen-bubble and frozen-bubble-data, but /usr/local/share/frozen-bubble is missing so the game won't start. I tried reinstalling, I tried purging, but nothing worked. What do I do?

---

### Post by hikaricore on 2007-03-21
Which version of frozen bubble are you using?  Try uninstalling and using this one.

[http://mirror.randumb.org/darkmagez/repo/pool/edgy-darkmagez/games/frozen-bubble_2.1.0-1_i386.deb](http://mirror.randumb.org/darkmagez/repo/pool/edgy-darkmagez/games/frozen-bubble_2.1.0-1_i386.deb)
[http://mirror.randumb.org/darkmagez/repo/pool/edgy-darkmagez/games/frozen-bubble-data_2.1.0-1_all.deb](http://mirror.randumb.org/darkmagez/repo/pool/edgy-darkmagez/games/frozen-bubble-data_2.1.0-1_all.deb)

and here's some music for it:

[http://mirror.randumb.org/darkmagez/repo/pool/edgy-darkmagez/games/fb-music-low_2.1.0-1_all.deb](http://mirror.randumb.org/darkmagez/repo/pool/edgy-darkmagez/games/fb-music-low_2.1.0-1_all.deb)

Hope this helps,

--Aaron

---

### Post by elreteipos on 2007-03-21
I installed Frozen Bubble from the Ubuntu repositories. They only offer the outdated 1.0.0-6ubuntu1, but I like that one more then the v2 branch. I should also say that I tried removing v2 manually because 'make uninstall' didn't work (I used the tarball). Then the old version I had on my computer for ages got all messed up so I tried reinstalling it, which as you know didn't work.

Anyways, I'll try the packages you listed here but if anyone knows how to make version 1.0.0 run again, please say so.

---

### Post by hikaricore on 2007-03-21
I'm guessing you still have the old binary from your make uninstall failure.  You'll need to track it down and remove it as well, other than that if you still get odd errors, make sure that fb doesn't have any config files in your home directory as they may be linking to the wrong data location. (the config file thing is just a guess, i havn't personally looked on my system)

Good luck,

--Aaron

---

### Post by elreteipos on 2007-03-22
Here's what I did to solve the problem: I removed the broken Frozen Bubble (1.0.0) packages, downloaded the v1.0.0 tarball from their website, applied a [patch](http://www.frozen-bubble.org/troubleshooting/), installed it and now everything works fine again.

---

