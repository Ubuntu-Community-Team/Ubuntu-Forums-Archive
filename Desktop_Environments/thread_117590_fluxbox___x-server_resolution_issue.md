---
title: "fluxbox  / x-server resolution issue"
date: 2006-01-15
forum: Desktop Environments
---

### Post by key on 2006-01-15
I have having a strange problem with kdm and my fluxbox screen resolution.

I have to specify the physical screen size for my dell inspiron laptop display in my xorg.conf file. No problem there - when kdm starts up, I log in and the resolution is 85dpi. Everything is correct. 

Now if I skip kdm and just log in from a terminal (my preferred login), the resolution is 100 dpi, which means I lose some precious screen real estate.

Any Ideas on why startx is not using the correct screen size even though it is in xorg.conf?

key

---

