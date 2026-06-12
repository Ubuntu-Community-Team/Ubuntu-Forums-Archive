---
title: "Strange Terminal/Emerald bug"
date: 2009-07-22
forum: Desktop Environments
---

### Post by JoyousDeath on 2009-07-22
This all started when this code

```
compiz --replace -c emerald &
```

Blew up in my face and after a flashing screen aborted prematurely. After this I entered emerald --replace which did nothing. I tried changing the System>Preferences>Appearance because I noticed that visual effects were turned off. I fixed this problem with this code.

```
gconftool-2 -s -t bool /apps/metacity/general/compositing_manager false
```

found here: [http://ubuntuforums.org/showthread.php?t=1204518&highlight=visual+effects+enabled#5](http://ubuntuforums.org/showthread.php?t=1204518&highlight=visual+effects+enabled#5)

I then turned visual effects back to the normal setting and tried emerald --replace again. Which worked except for one bug, I can't close the terminal. If I do, no theme is added at all and there is no title bar. 

Any ideas? :confused:

---

### Post by JoyousDeath on 2009-07-22
Some lovely IRC friends helped in the ubuntu support window. 

```
(emerald --replace &)
```

This fixes my specific problem, thanks to all who helped.

---

