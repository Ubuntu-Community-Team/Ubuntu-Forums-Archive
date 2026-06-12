---
title: "how do i fix the reversed window buttons?"
date: 2009-01-12
forum: General Help
---

### Post by Chrono Reaper on 2009-01-12
I originally posted this in the general help but i think this falls under the category more. 

My Problem:

I was viewing the packaging from the max4linux installation package [http://ubuntuforums.org/showthread.php?t=555373](http://ubuntuforums.org/showthread.php?t=555373) and accidentally clicked on the "install" file when viewing the files. now all my theme's windows has the minimize, maximize and close buttons are on the left side of the window rather than the right.

Here is an image of the problem:

[http://i418.photobucket.com/albums/p...creenshot1.png](http://i418.photobucket.com/albums/p...creenshot1.png)

How do I reverse this problem so that the buttons are no longer on the left side and back on the right side of the window?

---

### Post by earthpigg on 2009-01-13
from a terminal:

> gconf-editor

apps -> metacity -> general -> button_layout

make it read:

```
menu:minimize,maximize,close
```

---

