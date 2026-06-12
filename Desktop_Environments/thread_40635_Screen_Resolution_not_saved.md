---
title: "Screen Resolution not saved"
date: 2005-06-09
forum: Desktop Environments
---

### Post by carytid9 on 2005-06-09
After booting & logging on, I need to alter the Screen resolution  (System/Preferences/Screen resolution).  I check the box to make new resolution the default; the resolution changes OK, and remains so for the rest of the session.
However, when I reboot, the Screen Resolution is back to its original value.

There must be a config file somewhere which is not being saved?

---

### Post by knorr.orange on 2005-06-09
You could always manually modify the xorg config file....

as root, edit   /etc/X11/xorg.conf

look for:  Section "Screen"


Here is an example from one of my sections (for 24 bit color):

```

SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection

```


You will probably want to make a backup copy first so as not to do anything terrible.

---

