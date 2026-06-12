---
title: "Position of first opened window (not maximized)"
date: 2012-09-06
forum: Desktop Environments
---

### Post by vasa1 on 2012-09-06
Xfce 4.10 on Ubuntu 12.04.

With reference to apps running **non-maximized**, I notice that the first program I open opens in the top left corner of the screen. The next is aligned with the top right corner. Subsequent ones open at the bottom right and then the bottom left corner.

Is there a way to ensure or force the first app to open in the top right corner instead of the top left corner?

I'm asking because the icons on my desktop are on the left of the desktop. If I open Thunar, which takes up half the screen by default, it normally covers these icons. I then have to slide it horizontally if I want to see those desktop icons.

(When I say "top", I don't include the panel area which is always visible.)

---

### Post by vasa1 on 2012-09-14
Bump.
In short, when I open Thunar (file manager), it always opens in such a way that it occupies the **left**, vertical half of the screen.
I don't want that. I want Thunar to open so that it occupies the **right**, vertical half of the screen.

---

### Post by Toz on 2012-09-15
Hi vasa1.
I don't believe you can configure Xfce to direct exact placement of new windows. The best you can get using built-in Xfce configuration, is changing "Settings Manager -> Window Manager Tweaks -> Placement" and changing the "Be default, place windows" option to "Under the mouse pointer" and then running apps by right-clicking on the desktop where you want the window to open and using the application menu to start the application.

However, you could use a tool like devilspie to control window placement. For more info see: [http://www.foosel.org/linux/devilspie]("http://www.foosel.org/linux/devilspie").

For example, to get Thunar to always open on the right side of the screen, use a ds file like this:
```

(if
    (is (window_class) "Thunar")
    (begin
       (geometry "640x451-0+25")

    )
)

```
...(adjust geometry as required).

Make sure devilspie is running:
```

devilspie &
```
...and fire up thunar. It will be placed in the location specified by the geometry command in the ds file.

---

### Post by vasa1 on 2012-09-15
Toz, thanks for the pointer. I will look at devilspie.

Marking this solved.

---

