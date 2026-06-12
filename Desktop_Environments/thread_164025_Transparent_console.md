---
title: "Transparent console?"
date: 2006-04-22
forum: Desktop Environments
---

### Post by arachn1d on 2006-04-22
Hey all,

I'm trying to get a transparent aterm or whatever console there is.

the problem I'm running into is that the font looks horrible, all blocky and almost unreadable. 

here is my launch paramters.

aterm -name aterm -title 'Term' -sl 3000 -tr +sb -sr -si -sk -bg black -shading 60 -fade 90 -tn xterm
-g 130x50+20-0 -fg \#cecece 

I took it from some gentoo guide

---

### Post by louis_nichols on 2006-04-22
I think you're going about this the hard way. Terminal emulators like konsole and gnome-terminal are easily configurable, from the settings menu, to be transparent. You can also hide the menubar and scrollbar they have. Then you configure the window manager to hide the window border, and you'll have a nice looking transparent console.

I find gnome-terminal better suited for this, because konsole will always have a small border around the window, preventing it to blend into the desktop.

---

### Post by GoldBuggie on 2006-04-22
use konsole and go to settings. thee you can make it tansparent. But why not use Yakuake. You can set it to transparent as well and it drops down for usage when you press f12 and dissapears when you don't want it no more. Yakuake is a great move in the konsole buisness. Makes using the konsole much more integrated..

---

