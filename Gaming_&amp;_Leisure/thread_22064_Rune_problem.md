---
title: "Rune problem"
date: 2005-03-25
forum: Gaming &amp; Leisure
---

### Post by cdhotfire on 2005-03-25
I just got this game called Rune, and it installed well. But when i try to open it this is what comes out:
```
dirname: too few arguments
Try `dirname --help' for more information.
Couldn't run Rune (rune-bin). Is RUNE_DATA_PATH set?
```

any clues?

---

### Post by Slalomsk8er on 2005-03-31
```
$ killall -9 esd
$ rune +set fs_basepath /usr/local/games/rune
```

It works nearly for me ;)

---

### Post by cdhotfire on 2005-04-09
thxs, but its 1.07 thats no good, everyone that plays in 1.07 are noobs. :\

---

