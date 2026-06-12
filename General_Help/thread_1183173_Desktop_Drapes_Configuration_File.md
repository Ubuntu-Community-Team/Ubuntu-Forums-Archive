---
title: "Desktop Drapes Configuration File"
date: 2009-06-09
forum: General Help
---

### Post by ffixcollector on 2009-06-09
I need to delete all the pictures stored in desktop drapes and re-add them. Is there an easy way to delete them?

I can't find the configuration file, but if i knew where it was and deleted it, drapes should re-create a new one, correct?

---

### Post by ffixcollector on 2009-06-09
nobody knows where the configuration file is located?

---

### Post by notmyidea on 2009-06-21
Can't you just delete them by right-clicking the icon in the tray selecting preferences and remove?

There is an xml file associated with drapes under ~/.gconf/apps/drapes but it doesn't contain the files you are referring too (just the monitoring directory).

---

### Post by Lessss on 2009-11-10
Same issue.
Too many pics to remove manually, and it crashes before I can save and exit. Any that I manually remove come back next load.
Tried un-installing drapes and reinstalling. Files were still there.

Need to know the file that lists the directory or files to display.
Also need to know the upper limit of files that can be listed without crashing Drapes.

Had wallpapoz the last time I tried ubuntu and that crashed too.
This is the last bug to be worked out before I can abandon XP for ubuntu. I worked out the double vid card double monitor issues and sound issues. This is the last hurdle.
The files are on a separate hard drive.

---

### Post by Lessss on 2009-11-10
switched to wallpaper-tray, so far is working. Will need to see after a few log-ins/outs

---

### Post by johnblack on 2010-08-11
> **ffixcollector said:**
> I need to delete all the pictures stored in desktop drapes and re-add them. Is there an easy way to delete them?

I can't find the configuration file, but if i knew where it was and deleted it, drapes should re-create a new one, correct?

I found the configuration file of drapes at: /home/USER/.gnome2/drapes.xml.
And, yeap, you can delete this file, when drapes start, it will create a default file for you.

---

