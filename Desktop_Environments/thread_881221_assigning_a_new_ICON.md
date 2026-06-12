---
title: "assigning a new ICON"
date: 2008-08-05
forum: Desktop Environments
---

### Post by sandman3838 on 2008-08-05
Hello

When you go into SYSTEM - PREFERENCES - APPEARANCES and then select custom there is an option TAB for ICONS.  I have about twenty now.  Some I like and some I don't.  Some I really like but fail to alter the FIREFOX Icons.  They are just left there with some awful generic icon.  Is there a way to change the ICON assigned for a particular file.  In this case I would like to change the URL icons globally?

Is there a program of some file I should edit?

Thanks for your time.

---

### Post by pauper on 2008-08-06
Firefox is not integrated into gtk themes. It keeps its icons separately.
Overwrite recursively default Firefox icons with custom in these locations:
/usr/share/firefox/chrome/icons/default and /usr/share/firefox/icons.
Make sure to match file names. Will have to do every time after firefox update.
Restart browser.

---

