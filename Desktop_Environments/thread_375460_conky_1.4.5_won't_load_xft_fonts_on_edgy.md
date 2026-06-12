---
title: "conky 1.4.5 won't load xft fonts on edgy"
date: 2007-03-03
forum: Desktop Environments
---

### Post by foormea on 2007-03-03
i'm running edgy
i've compiled conky 1.4.5 with xft support, conky -v says xft support is enabled

my .conkyrc file contains these:

> use_xft yes
xftfont Bitstream Vera Sans Mono:size=8
font arial

and i don't use any $font later in the config file

the xft font i wanna use is installed, it's listed in fx-list

but conky won't load it. it won't load any xft font in fact

heeellllllp please :)

---

### Post by foormea on 2007-03-04
i could solve my problem: put the correct font path in xorg.conf, mkfontdir, and not use a "font <whatever>" in .conkyrc if "use_xft yes" and "xftfont <whavever>"

---

### Post by foormea on 2007-03-04
i could solve my problem: put the correct font path in xorg.conf, mkfontdir, and not use a "font <whatever>" in .conkyrc if "use_xft yes" and "xftfont <whavever>"

---

