---
title: "How to have a virtual screen on Dell mini9"
date: 2009-01-01
forum: Desktop Environments
---

### Post by fsierra3 on 2009-01-01
Hello, I have an Inspiron mini9 which comes with a display that has a native resolution of 1024x600, and I would like to have a virtual screen (something similar to the magnifying utility that starts when you press Super+2 or 3) with a higher resolution, say 1024x768 to get around the problem of windows showing themselves bellow the bottom panel. I did some search on the Internet and this is what I tried:

1)typed in a terminal: gksu gedit /etc/X11/xorg.conf
2)Added these lines in the section “Screen”
SubSection “Display”
Virtual 1024 768
EndSubSection
3)Restarted X (ctrl+alt+backspace)

But it didn't work. I thought I needed to activate the virtual screen using the Screen Resolution Preferences, but the drop down list doesn't show the 1024x768 option.

I wold like to thank beforehand any help, and apologize for any spelling or grammar mistake (English is not my native language)

---

