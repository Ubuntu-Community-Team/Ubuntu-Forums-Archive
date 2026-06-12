---
title: "How to increase font size of Oracle SQL Developer?"
date: 2009-05-30
forum: Desktop Environments
---

### Post by jegan21 on 2009-05-30
I just installed the latest Oracle SQL Developer client under Ubuntu 9.04.  I can change the font size of the editor, but I cannot change the font size of the application itself, e.g., the menus, dialogs, etc.  I tried changing the default font size of EVERHTHING in the ide.properties file, to no avail (See below).  How can I change the font size of the application?

-Thanks

Ide.FontSize=14
##   Ide.FontSize=11
#
# To modify the font size for a particular look-and-feel in all
# locales, set the Ide.FontSize.<lafID> property.  For example:
Ide.FontSize.Aqua=14
Ide.FontSize.Metal=14
Ide.FontSize.Motif=14
Ide.FontSize.Oracle=14
Ide.FontSize.Windows=14

---

### Post by Vadi on 2009-05-30
Are you sure there is only one such file?

---

### Post by jegan21 on 2009-05-30
Actually, that did work.  The problem was that setting the font to 14 did not result in a large enough increase in size, in my case.  I changed it to 17, and it looks much better.

---

### Post by jegan21 on 2009-05-30
> **Vadi said:**
> Are you sure there is only one such file?

That was one of my first thoughts, so I did a sudo updatedb, and then locate ide.settings, to look for a system-wide settings file.  The problem was that setting the font to 14 was not enough for me to notice the difference.  I set it to 17 and it looks larger.

-Thanks

---

### Post by Vadi on 2009-05-30
Glad you got it.

---

