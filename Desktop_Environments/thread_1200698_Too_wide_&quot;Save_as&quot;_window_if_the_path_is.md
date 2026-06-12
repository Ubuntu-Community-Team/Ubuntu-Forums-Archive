---
title: "Too wide &quot;Save as&quot; window if the path is long"
date: 2009-06-30
forum: Desktop Environments
---

### Post by winz on 2009-06-30
Hi,

I have a problem when saving files through "Save as" menu to samba shares with Russian directory names in the path. The "Save as" windows get too wide and you can't even reach the OK/Cancel buttons. Look the screenshot attached.

[IMG]http://i39.tinypic.com/9h6lc8.png[/IMG]

Is there a fix for this problem? Please, advise.

Thanks.

---

### Post by mcduck on 2009-06-30
Alt-left mouse button allows you to move the window from any point in the window (not just titlebar like usually) and Alt-middle button resizes the window in similar way.

---

### Post by winz on 2009-06-30
Thanks! I can move the window, but I can't resize it. And it's like 50 times a day I have to move-move-move it to reach the buttons. I can just press enter to click OK, but sometimes it can be "Cancel". That's the problem.

---

### Post by beilman on 2009-09-10
I'm having the exact same problem.  I first noticed it in Gimp but it has happened with other programs' save as window.  Any new info on what's causing this?  It will let me resize the save as window to make it wider than it already is, but not narrower.  It's really a pain.  Thanks for any help.  Oh, and my profile is wrong, I'm running 8.04.

---

### Post by mcduck on 2009-09-11
> **beilman said:**
> I'm having the exact same problem.  I first noticed it in Gimp but it has happened with other programs' save as window.  Any new info on what's causing this?  It will let me resize the save as window to make it wider than it already is, but not narrower.  It's really a pain.  Thanks for any help.  Oh, and my profile is wrong, I'm running 8.04.

If you open the dialog with a very long path (like the "save in folder" in the screenshot above) the dialog window tries to resize into large enough size to fit that path..

Resizing into smaller size usually doesn't work since most programs don't allow resizing windows into smaller than the minimum space that's able to contain all the window's widgets..

---

### Post by beilman on 2009-09-11
I don't think that the path is too long.  Unless i'm missing something, there is something else going on here:
[IMG]http://www.beilmanfabrication.com/Screenshot.png[/IMG]

---

### Post by Wardje on 2009-09-12
> **beilman said:**
> I don't think that the path is too long.  Unless i'm missing something, there is something else going on here:
[IMG]http://www.beilmanfabrication.com/Screenshot.png[/IMG]

If it goes really wide once, it remembers that size for next time it gets opened (or so I seem to recall). So you'll have to resize it to something smaller and then it should be ok. Until the big one gets opened again I guess. I've experienced it myself when uploading to Photobucket (or some other image site) and agreed, it's a pain.

---

### Post by beilman on 2009-09-12
Thanks for the help.  Ok, I figured what path was too long.  It wasn't that the "save as" path was too long but there was a path in the "Places" portion of the window that was really long but i just couldn't see the whole path.  That was causing the window to be so wide.  I removed that location from the "places" area and the window resized as it should have.  Thanks again for the help

---

### Post by winz on 2009-11-06
It seems to be fixed in 9.10, though - the path doesn't make save-as windows go wider. But, the problem with windows, that have long lines of text in it, still exists.

---

