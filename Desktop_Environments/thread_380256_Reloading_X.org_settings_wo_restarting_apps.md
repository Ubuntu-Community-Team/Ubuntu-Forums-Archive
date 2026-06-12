---
title: "Reloading X.org settings w/o restarting apps"
date: 2007-03-09
forum: Desktop Environments
---

### Post by Jmccaffrey on 2007-03-09
I want to reload xorg.conf without changing the state of my programs that use X, is this possible?

---

### Post by invalid on 2007-03-09
edit: sorry, I mis-read this post..

---

### Post by Jmccaffrey on 2007-03-09
> **invalid said:**
> edit: sorry, I mis-read this post..

Yea, allow me to clarify, I wish to preform a windows/mac style settings change, where I select, say a new resolution, and then my screen changes to that new setting without having to restart anything.  Is that possible through either a utility or an API call directly to the X server?  If it is not possible, why has this not been implemented, is there a technical reason barring this kind of feature?

---

### Post by motin on 2008-01-26
> **Jmccaffrey said:**
> Yea, allow me to clarify, I wish to preform a windows/mac style settings change, where I select, say a new resolution, and then my screen changes to that new setting without having to restart anything.  Is that possible through either a utility or an API call directly to the X server?  If it is not possible, why has this not been implemented, is there a technical reason barring this kind of feature?

Yes it is certainly possible, the trick is to change your xorg.conf then start a new X session on the fly - it will use the new configuration.  I just wrote a Howto on this: [http://ubuntuforums.org/showthread.php?p=4211618](http://ubuntuforums.org/showthread.php?p=4211618)

---

### Post by kjetilho on 2008-01-26
In general, it is not possible (the HOWTO referenced in the other reply starts a **new** session).  Some stuff can be changed on the fly, though, actually most of the stuff you find in Display Settings in MS Windows: fonts and sizes, screen resolution and so on.  Specifically for changing the resolution, check out xrandr.

---

