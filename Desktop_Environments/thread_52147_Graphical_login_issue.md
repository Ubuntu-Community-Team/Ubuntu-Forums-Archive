---
title: "Graphical login issue"
date: 2005-07-26
forum: Desktop Environments
---

### Post by Ruskie on 2005-07-26
Hello, I have this problem at login.
After having played a while with GNOME screen resolution, I've managed to run it at 1024x768 by default (instead of the original 1280x800). Now, putting this resolution as first in "Modes" lines, it works, and the desktop is sized appropriately.

However, the login screen that appears when you boot linux, still has a greater size: it's still at 1280x800, so when it is showed on my smaller screen it overflows the borders and I have to scroll to reach outer portions of it! How can I automatically resize it to the screen resolution?

Any help appreciated, thank you!
Marco

---

### Post by Xian on 2005-07-26
I would place "1024x768" first for each of the Depths listed in the xorg.conf.

---

### Post by Ruskie on 2005-07-26
[QUOTE=Xian]I would place "1024x768" first for each of the Depths listed in the xorg.conf.[/QUOTE]
 I did. That's why now the login screen appears bigger. When I had 1280x800 as first configuration, it was displayed at full screen, being as big as the screen.
Now the screen is "smaller", that's why the login screen overflows.
I need to resize the login screen rather than changing the monitor resolution...

---

### Post by Xian on 2005-07-26
AFAIK there is not a separate config to resize the login screen.

---

### Post by Ruskie on 2005-07-27
[QUOTE=Xian]AFAIK there is not a separate config to resize the login screen.[/QUOTE]
 Well, thanks for trying. :) If anybody else has suggestions, I'd be grateful.

---

### Post by Vilius on 2006-06-05
Exactly the same problem, picture is larger than resolution.
How to fix that ???????????????????????????????????

---

### Post by hanexar on 2006-06-06
[QUOTE=Vilius]Exactly the same problem, picture is larger than resolution.
How to fix that ???????????????????????????????????[/QUOTE]


Try this out:
[http://www.ubuntuforums.org/showthread.php?t=190081&highlight=login+screen+resolution](http://www.ubuntuforums.org/showthread.php?t=190081&highlight=login+screen+resolution)

---

