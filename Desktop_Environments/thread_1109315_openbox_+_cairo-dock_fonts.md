---
title: "openbox + cairo-dock fonts"
date: 2009-03-28
forum: Desktop Environments
---

### Post by lykwydchykyn on 2009-03-28
Just for a change of pace, I decided to use openbox for a while.  I'm also running cairo-dock with xcompmgr providing the compositing.  It all works fairly well together, but for some reason cairo-dock is utterly ignoring my attempts to change fonts.  I can go into the settings for cairo-dock or any individual widgets, and try to set fonts until I'm blue in the face, but it just keeps using the same default sans-serif font.

I cleared .xsession-errors and tried to change the fonts via cairo-dock=>configure=>dialogs=>text, and here was the output:
```

add CD box
add scotch
add frame&reflects
add dark
add none
add frame with scotch
add clear
cairo_dock_window_is_fullscreen_or_hidden_or_maximized ()
changement d'etat de 18916741 => {0 ; 0 ; 0 ; 0}
  MaJ des decorations du fond -> 1962.00x43.00

```

Anyone know if this works.

---

