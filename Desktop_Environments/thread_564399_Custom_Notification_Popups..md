---
title: "Custom Notification Popups."
date: 2007-10-01
forum: Desktop Environments
---

### Post by jonny_sicoli on 2007-10-01
First off, i would like to say that for a free desktop, Ubuntu is incredibly customizable.  However, after a complete desktop makeover, the little yellow system notifications seem to stay the same.  I don't want to get rid of them, just change the image so that they better fit the system theme.  If anyone has some premade system popups that I can just apply, that'd be nice.  Also, if anyone has any idea on how to change the text inside the boxes, that'd be nice to know also.

And now for your enjoyment a yellow thing waving a disproportionate sign.
:lolflag:

---

### Post by Khaine on 2007-10-01
Yes you can change the style of the libnotify pop-up

[http://ubuntuforums.org/showthread.php?t=328795&page=2](http://ubuntuforums.org/showthread.php?t=328795&page=2)

1. List contents of folder /usr/lib/notification-daemon-1.0/engines to see what you have to choose from. I have such files:
libbubble.a libbubble.so libstandard.la libubuntu.a libubuntu.so libbubble.la libstandard.a libstandard.so libubuntu.la
Which means I have 3 themes to choose from: bubble, ubuntu and standard.
2. Launch gconf-editor. Find node /apps/notification-daemon and edit key "theme". I changed the default value "ubuntu" to "standard".

---

### Post by jonny_sicoli on 2007-10-03
Thank you! However, i'm kinda disappointed about the selection.  Is there a custom libnotify site around?

---

