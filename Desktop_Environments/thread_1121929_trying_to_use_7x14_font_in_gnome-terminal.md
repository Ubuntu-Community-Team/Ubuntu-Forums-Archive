---
title: "trying to use 7x14 font in gnome-terminal"
date: 2009-04-10
forum: Desktop Environments
---

### Post by ibanex22 on 2009-04-10
Hi,

I'm trying to use the 7x14 font in gnome-terminal with no luck.  It isn't in my font list when I go into my Default profile, I cannot set it manually via gconf-editor as '7x14' (the terminal comes up with a blank font when I do that).  I can however, run 'emacs -font 7x14' which loads emacs with the 7x14 font so I know I have it somewhere.  I can also use xterm with 7x14.

I've tried to enable bitmapped fonts with 'sudo dpkg-reconfigure fontconfig-config' but it's still not in my font list.

I have also tried to add a directory of fonts to /usr/share/fonts/truetype filled with the 7x14 pcf.gzs and reinit my font cache with no luck either.

Any help or clues would be greatly appreciated.

Thanks,
Erik

---

