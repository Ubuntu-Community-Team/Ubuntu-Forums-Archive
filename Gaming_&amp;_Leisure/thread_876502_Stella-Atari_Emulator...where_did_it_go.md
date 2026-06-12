---
title: "Stella-Atari Emulator...where did it go???"
date: 2008-07-31
forum: Gaming &amp; Leisure
---

### Post by jukingeo on 2008-07-31
Hello all,

I just installed Stella, the Atari 2600 emulator into Ubuntu Studio.  The install seemed to go well through Synaptic...but unlike other emulators I installed, the launch icon doesn't appear in games.  Where did it install to then?  How can I launch it?

Thanx,

Geo

---

### Post by BigSilly on 2008-08-01
Thanks for the heads up! I installed this, then completely forgot I had. You're right it's not in the menu. Open a terminal and type:

```
stella
```

That'll bring it up. It's easy enough to manually add an icon to launch it from your menu. You can do it via the Main Menu setting in System/Preferences. Create new item in the Games menu, and browse to the command in usr/bin/stella, and it will automatically put the correct icon in place.

This is what I've just done anyway. Hope it helps.

---

### Post by jukingeo on 2008-08-01
> **BigSilly said:**
> Thanks for the heads up! I installed this, then completely forgot I had. You're right it's not in the menu. Open a terminal and type:

```
stella
```

That'll bring it up. It's easy enough to manually add an icon to launch it from your menu. You can do it via the Main Menu setting in System/Preferences. Create new item in the Games menu, and browse to the command in usr/bin/stella, and it will automatically put the correct icon in place.

This is what I've just done anyway. Hope it helps.

Thanx for the info, that worked.


[SOLVED]

However, Stella looks really really different now.  I had Ubuntu before with Stella, but it was a gui interface, this is all text.  Then again I am not sure anymore how I installed the first one.  I could have done it from the Stella site.

...Ok, I found out where I got it from.  Here is a .deb file on Sourceforge:

[http://sourceforge.net/project/showfiles.php?group_id=41847](http://sourceforge.net/project/showfiles.php?group_id=41847)

This one has the graphic interface.

However thank you for the tip on editing/creating menu items.

Geo

---

