---
title: "title bar goes away after emerald -replace"
date: 2007-12-11
forum: Desktop Effects &amp; Customization
---

### Post by Jgryder on 2007-12-11
ok I followed some advice on a thread to fix the title bar going away when using emerald themes.  but when I close the terminal it makes the title bars go away again.

---

### Post by smartboyathome on 2007-12-11
The reason the title bars go away is because no window decorator is running. To run one, use alt+f2 and then run emerald --replace.

---

### Post by Kevanx on 2008-06-22
I have this same problem.
Emerald isn't reading a transparent the transparency fo a theme for some reason, and if I do emerald --replace, then it works fine, until I close the terminal window.
Similarly, when previously trying to game under wine, I would run
metacity --replace.
That worked fine, but when I did compiz --replace at the end, then it switched back to compiz UNTIL the terminal was closed, at which point the menu bars would disappear, and windows would be anchored at the top left of the screen.

Any help would be greatly appreciated.

*EDIT: I don't know what changed, but doing alt-f2 and typing emerald --replace works fine for me now.*

---

