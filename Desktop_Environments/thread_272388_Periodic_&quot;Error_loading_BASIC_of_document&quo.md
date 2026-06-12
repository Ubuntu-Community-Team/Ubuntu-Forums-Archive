---
title: "Periodic &quot;Error loading BASIC of document&quot; while using OpenOffice Calc"
date: 2006-10-06
forum: Desktop Environments
---

### Post by Ubuntist on 2006-10-06
Lately while using OpenOffice.org 2.0's Calc spreadsheet, I've found that a few times an hour an error box pops up saying:

```

Error loading BASIC of document
file:///home/ubuntist/.openofficeorg2/user/basic/Standard/Module1.xba:
General Error.
General input/output error.
```

Calc still seems to work fine, but the messages are a nuisance and I worry that there is some deeper problem lurking somewhere.

Would anyone have an idea what would cause this problem and what I should do about it?

---

### Post by Ubuntist on 2006-10-16
I found the solution in the Calc forum on [http://www.oooforum.org]("http://www.oooforum.org").

In playing around with OOo macros some time ago, I had created a macro module which no longer existed.  It was merely necessary to delete the reference to the module using the Tools|Macros|Organize Macros|OpenOffice.org Basic, select, in my case "Module1" and click Organiser... and then Delete.

---

