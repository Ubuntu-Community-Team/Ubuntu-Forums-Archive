---
title: "Unable to set Image Viewer in Defaults for LXSession"
date: 2016-04-24
forum: Desktop Environments
---

### Post by nadrach on 2016-04-24
I have been using Lubuntu since 12.04, 32-bit and 64-bit, and have just installed 16.04 64bit.
All this time there has been a glitch in the LXDE menu for setting the "Default applications for LXSession" on the choice for "Image viewer". It does not stick beyond the current session.
You can set a value (in my case just the standard "Image Viewer") and this is fine until you shut down. On restart/boot, the setting reverts to "Disable".
What I have also just found (and checked back on 14.04 on a machine not yet re-installed) is that if you have GIMP installed, it is not listed as an option.

Any reason(s) why?

---

### Post by vasa1 on 2016-04-24
> **nadrach said:**
> I have ... just installed 16.04 64bit.
... What I have also just found (and checked back on 14.04 on a machine not yet re-installed) is that if you have GIMP installed, it is not listed as an option.

Any reason(s) why?
GIMP shows up in lxpanel's main menu under Graphics for me. It also shows up when I right-click an image file in PCManFM and choose Open with ...

---

### Post by nadrach on 2016-05-15
Not a problem there, where I am looking is in the default setup for LXSession Configuration: "Preferences/Default applications for LXSession/Launching applications/Image Viewer". This always returns to "Disable" on shutdown. This is what sets the default (first in the list) for "Open With". GIMP is not an option here.

---

