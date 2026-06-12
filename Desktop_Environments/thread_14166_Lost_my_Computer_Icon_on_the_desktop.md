---
title: "Lost my Computer Icon on the desktop"
date: 2005-02-05
forum: Desktop Environments
---

### Post by montgomj on 2005-02-05
As the title indicates, I want to get the Computer Icon back on the desktop.  I do not remember removing it, deleting it or anything like that.  Any ideas on how to do this?

Thanks in advance.

---

### Post by carlc on 2005-02-05
This should work:

Click - Applications
Click - System Tools
Click - Configuration Editor

Expand - apps
Expand - nautilus
Expand - desktop

Check - computer_icon_visible

---

### Post by montgomj on 2005-02-05
Thanks for this; I am not very familiar with the gconf tool (yet).  I followed your post and the icon is there.  However, it has no name.  Went back to gconf and made sure the comuter_icon_name was also checked at it was.  So went to the desktop icon and checked its properties.  Under Name the dialog box is greyed out and I cannot edit it.  I think I may have to do this as root, somehow.  But I am up and working with the icon and your post has helped a lot.

Thanks very much.

---

