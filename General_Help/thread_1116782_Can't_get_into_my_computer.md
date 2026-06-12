---
title: "Can't get into my computer?"
date: 2009-04-05
forum: General Help
---

### Post by super-sauce on 2009-04-05
Whenever I go to my home folder, or computer, or try to mount another hard drive, ubuntu will just say "opening home" or "opening computer" and then after a few moments it will disappear and not open.  I have to have access to my computer and cannot figure out what is going on can someone please help me?  I'm using ubuntu 8.10 and i cannot get to any location period.... totally blows.

---

### Post by fooman on 2009-04-05
try opening nautilus from a terminal window.  that way it will spit out any errors for you to see what the problem is.

open a terminal....go to applications > accessories > terminal

when the terminal opens,  type:

```
nautilus
```and press enter...see what errors pop up (if any) and post them back here.

---

### Post by super-sauce on 2009-04-05
okay sorry i think i figured it out, I was previously trying to get my trash icon to show up on my desktop, and i went into gconf-editor and un-checked the "show trash icon" box, now it's working again.  For some reason when I have "trash icon visible" selected, not only does it not show the trash, but it keeps nautilus from being able to open a location.  Here is the output of the terminal code:

seahorse nautilus module initialized
Initializing nautilus-share extension

** (nautilus:6847): WARNING **: Cannot extract frame (252, 0) from the grid


** (nautilus:6847): WARNING **: Unable to add monitor: Not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

---

