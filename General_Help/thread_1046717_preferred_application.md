---
title: "preferred application"
date: 2009-01-21
forum: General Help
---

### Post by Bigneil on 2009-01-21
totem movie player is default, but i can't get it to play dvd'd  but i have Mplayer Movie Player which does. how do i make Mplayer default ?

i tried choosing custom and typing Mplayer in the box provided i also tried to drag and drop it there.   

Is there a command that i need?


Any one help??


either that or help to get Totem playing DVD's

---

### Post by taurus on 2009-01-21
Don't you need to install libdvdcss2 first before you can play a movie on your machine?

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

And if you want to use totem, I think you have to use gxine engine.  It should be available from synaptic.

---

### Post by mc4man on 2009-01-21
You should really post what version of ubuntu your using, the methods for setting a default for dvd's is slightly different.
You are looking in the wrong place, for hardy and intrepid the setting is made in 'file management' -> media

Lots of ways to get there
r. click on Applications -> edit menus and enable in preferences menu

home folder (nautilus) edit -> preferences

from terminal
```
nautilus-file-management-properties
```

Totem-gsteamer isn't well suited for movies, maybe install totem-xine 

Setting new defaults is very easy in Intrepid, Hardy requires some add. steps depending on the app


For instance for gmplayer you need to have it launch with 
gmplayer dvd://

In Intrepid from the dvd movie drop down in preferences -> media, you'd simply choose 'use other application' -> 'use a custom command' and insert above
(smplayer is better than the default gmplayer and once installed can be set in that drop down by either choosing from the list or with a custom command of
smplayer

---

