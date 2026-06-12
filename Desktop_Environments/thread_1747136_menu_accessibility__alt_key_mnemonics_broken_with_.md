---
title: "menu accessibility / alt key mnemonics broken with custom .xmodmap in natty"
date: 2011-05-02
forum: Desktop Environments
---

### Post by eitan on 2011-05-02
hello,
 i upgraded to natty.
 i'm also used to using alt-f and so on to access menus using the keyboard.
 i verified this works by default.
 however, i always customize my desktop with an xmodmap file because i like the ctrl key to map to my thumb.  this means i swap alt, control, and super keys as follows:

!
! Setup keys so that control is nearest thumb, then moving left: alt, and finally super
!

remove mod1 = Alt_L
remove mod4 = Super_L
remove control = Control_L

keysym Alt_L = Control_L
keysym Super_L = Alt_L
keysym Control_L = Super_L

add mod1 = Alt_L
add mod4 = Super_L
add control = Control_L



when i do this, alt key mnemonics no longer works.  alt+f no longer gives me access to the file menu.

any ideas for mapping meta keys perhaps in another manner that doesn't conflict with natty?

thanks in advance,
/ eitan

---

### Post by eitan on 2011-05-02
i thought i'd also note that it's not just the menu mnemonics that fail, but other keyboard shortcuts with alt key combinations.  namely:

- alt-1, alt-2, etc.. for tab switching in web browsers or gedit no longer work.
- alt-left arrow in a browser or in eclipse for going back to previous page / previous edit does not work.

---

### Post by eitan on 2011-05-03
solved.
i futzed around with .xmodmap and found a configuration that worked.

revising these:

remove mod1 = Alt_L
remove mod4 = Super_L
remove control = Control_L

with these:
clear mod1
clear mod4
clear control

seems to have done the trick.

---

