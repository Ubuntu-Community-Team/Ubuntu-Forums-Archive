---
title: "Location of window triad"
date: 2010-11-18
forum: Desktop Environments
---

### Post by hutsky on 2010-11-18
I just upgraded from Ubuntu 9.10 to 10.04 and notice that the Close, Park, and Fullscreen Triad on each displayed window is located at the upper left corner.  I am accustomed to seeing it on the upper right.  Is this something fixed in the new version or is it something that can be changed?

This is not a big deal but will take some getting used to.

---

### Post by asmoore82 on 2010-11-18
That caused quite a stir leading up to Ubuntu 10.04 LTS.

Simply changing the theme under "Systems -> Preferences -> Appearance"
will move the buttons to that theme's preferred position.

You can also manually override this in the Configuration Editor:
```
gconf-editor /apps/metacity/general/button_layout
```

---

### Post by hutsky on 2010-11-18
asmore82, thanks for the response.  I suspected there may be some remedy but am rather new to Ubuntu.

---

