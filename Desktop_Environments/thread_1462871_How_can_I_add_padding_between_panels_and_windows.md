---
title: "How can I add padding between panels and windows"
date: 2010-04-26
forum: Desktop Environments
---

### Post by null_pointer_us on 2010-04-26
How can I add padding between panels and windows?

To explain, my setup uses four panels:

[LIST]
[*]left: Docky (large) for browsing windows by app icon
[*]right: panel (large) for browsing windows by virtual desktop
[*]top: panel (small) with system menu and notification icons
[*]bottom: panel (small) containing status and system management applets[/LIST]

Naturally, app windows occupy the center of the screen. For major applications like Firefox or an IDE, I want the app window maximized.

Aesthetically, I want the application windows separated from the panels so that the user's focus is on the application.

What I'd like is some space between panels and window edges, so that windows snap or maximize like 5-10px away from any panel instead of 0px. This would also make the wallpaper a little more visible.

---

### Post by null_pointer_us on 2010-04-28
(bump)

Adding blank panels does not accomplish this. Even when the blank panel backgrounds are set to solid color/transparent, the edges retain the grab bar images, which looks ugly.

Searching for gconf keys and .gtkrc stuff revealed nothing.

```

           [PANEL]
   -b-l-a-n-k---s-p-a-c-e-
   -l-=================-c-
   -a-| MAX'D APP.    |-a-
[D]-n-| WINDOW        |-p-[P]
[O]-k-|               |-s-[A]
[C]---|               |---[N]
[K]-s-|               |-k-[E]
[Y]-p-|               |-n-[L]
   -a-|               |-a-
   -c-|_______________|-l-
   -e-c-a-p-s---k-n-a-l-b-
           [PANEL]

```
8-[

Some illustration for you.

---

### Post by beruic on 2010-08-11
I am looking for the same. Found a solution yet?

---

