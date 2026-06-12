---
title: "Plus sign low (subscript) in terminal"
date: 2005-10-14
forum: Desktop Environments
---

### Post by avc on 2005-10-14
Just installed Breezy Badger. On terminal, the plus sign (+) appears subscript, lower than the rest of the text. I'm using the default font (monospace). When I switch fonts, the plus sign appears correctly.

I know this is a minor bug, but it sure is bugging me! What can be causing this?

---

### Post by avc on 2005-10-21
Anyone else having gnome-terminal font problems? I've switched to xterm now because of that annoying + sign.

---

### Post by avc on 2005-11-22
Fixed! I ran "dpgk-reconfigure locales" and installed en_US.UTF-8. Then I set /etc/environment to:
```
LANGUAGE="en"

LANG=en_US.UTF-8
```
and rebooted. No more font problems with gnome-terminal or fluxbox. Fluxbox wasn't displaying fonts (e.g. "glisp") on some themes. Now it all works.

---

