---
title: "nautilus display different from ls output on /usr/share/applications"
date: 2016-12-30
forum: Desktop Environments
---

### Post by alain-de-feyter on 2016-12-30
I was trying to dig into the launcher entries, e.g. to find where they are, scripts if any, etc. 
The output of nautilus for /usr/share/applications is very different from the output of ls /usr/share/applications:
ls lists a lot of .desktop files. none of these can be seen in the nautilus display.
the two outputs are shown in the attachments to this message.

These seem to be different directories. Any explanation for this inconsistency?

alain

---

### Post by mc4man on 2016-12-30
ls shows the actual file name, Ex. - nautilus.desktop
Nautilus shows whatever is on the Name= line in a .desktop file, Ex. - Files

---

