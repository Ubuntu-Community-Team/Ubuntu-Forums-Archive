---
title: "enabled all desktop settings in kubuntu - now get black screen"
date: 2009-02-25
forum: Desktop Environments
---

### Post by audience of one on 2009-02-25
enabled all desktop settings(widgets?) in KDE - now get black screen.
I did an ctrl alt f2, and am at command line.  where do I go to put my desktop back to the way it was??????

---

### Post by audience of one on 2009-02-25
Fixed!!!!!! :popcorn:    :guitar:

edited the file
~/.kde4/share/config/kwinrc

Find the section "[Compositing]" and then the value "Enabled" make sure it is set to "false"
You should then be able to login to KDE.
rebooted, now KDE is back sweet!

---

