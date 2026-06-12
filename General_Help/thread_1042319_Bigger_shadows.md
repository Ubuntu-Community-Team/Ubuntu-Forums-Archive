---
title: "Bigger shadows?"
date: 2009-01-17
forum: General Help
---

### Post by Fzang on 2009-01-17
Is there a way to make the shadows much bigger than the current maximum (we're talking OS X big)? There has to be, through some editing perhaps?

---

### Post by Ben Webber on 2009-01-17
If you have not yet, install CCSM (CompizConfig Settings Manager).

```

sudo apt-get update
sudo apt-get install compizconfig-settings-manager
```

Once that is installed, go to System > Preferences > Compiz Config Settings Manager.

Under "Effects", select "Window Decoration". Here you can tweak all the shadow settings.

---

### Post by Wartender on 2009-01-17
in compizconfig settings manager, in the window decorations plugin are all the settings for shadows.

---

### Post by Fzang on 2009-01-17
I know I can do that, and radius is max, at 18K. But these shadows aren't big at all! Can I somehow remove the 18k lock to raise it even further? I removed the min. wave lock with genie lamp animation so instead of the original 3 I can now set it down to 0. Can I do this with shadow radius as well with a hex edit?

---

### Post by Wartender on 2009-01-17
18,000 pixels????? that's ridiculous! that's 10 times bigger than your screen resolution!!

---

### Post by Fzang on 2009-01-17
Haha, no not pixels

18000 in "compiz parameters" which is... 18 pixels if GIMP serves me right :)

I tried opening libdecoration.so and found some options about shadows and found things like X and Y offset I could edit... but no value like "max 18000" or even 18 pixels

---

### Post by Fzang on 2009-01-17
Found the little critter :D

/usr/share/compiz/decoration.xml and edit the shadow radius from 18 to some high number

:)

---

