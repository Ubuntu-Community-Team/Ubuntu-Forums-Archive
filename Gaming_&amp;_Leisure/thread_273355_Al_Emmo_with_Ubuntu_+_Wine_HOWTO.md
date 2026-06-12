---
title: "Al Emmo with Ubuntu + Wine HOWTO"
date: 2006-10-07
forum: Gaming &amp; Leisure
---

### Post by scobes on 2006-10-07
Okay, Al Emmo runs okay with a plain wine installation but the videos don't play and you can't use the keyboard, you also can't use the mouse unless you play in a desktop.  So here's how to make it work properly.

First you'll need a patched version of wine.  The mouse patch I found... somewhere... and the keyboard patch I made based on an email on the wine-bugs list.  These patches probably work on newer versions of wine, but they're tested on 0.9.5.  So download wine:

```
wget http://ibiblio.org/pub/linux/system/emulators/wine/wine-0.9.5.tar.bz2
```

and get the patches attached to this message, save them all in your home directory.

open a terminal (if you don't already have one open) and type:

```
tar xfvj wine-0.9.5.tar.bz2
cd wine-0.9.5/dlls/dinput
patch -i ~/mousehack.diff.txt
patch -i ~/keyboard_hack.diff.txt
cd ..
cd ..
```

and compile wine with a simple:

```
./configure
make depend && make
sudo make install
```

Follow the howto at [http://www.ubuntuforums.org/showthread.php?t=149585](http://www.ubuntuforums.org/showthread.php?t=149585) except for the part about installing wine to get media player set up (it comes with IE) so the videos will work.

Now Bob's your uncle!

If it still doesn't work, try using winecfg to make wine run in a virtual desktop.  Any problems, post here and maybe someone who knows more than me will help you.

---

### Post by menachem on 2007-02-22
I was thinking of purchasing this game, and was wondering if wine now supports Al Emmo out of the box.

Thanks.

---

