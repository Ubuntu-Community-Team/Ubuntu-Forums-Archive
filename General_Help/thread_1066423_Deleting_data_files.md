---
title: "Deleting data files"
date: 2009-02-10
forum: General Help
---

### Post by JonWhite on 2009-02-10
I'm a new user.  This should be fairly simple, but the solution has eluded me to date.
I accidentally copied a data folder onto my desktop that I do not want. Now it is just hogging memory space.  I deleted it and sent it to the trash folder. 
It was protected and the trash file browser will not let me delete the file.  I checked the folder's permissions.  I own the file, but do not have permission to create or delete.  The file browser won't let me do that delete.  It says "Sorry, could not change the permissions of "XXXX": Operation not supported by backend."
Thanks in advance for the help.

---

### Post by dcstar on 2009-02-10
> **JonWhite said:**
> I'm a new user.  This should be fairly simple, but the solution has eluded me to date.
I accidentally copied a date folder onto my desktop that I do not want. Now it is just hogging memory space.  I deleted it and sent it to the trash folder. 
It was protected and the trash file browser will not let me delete the file.  I checked the folder's permissions.  I own the file, but do not have permission to create or delete.  The file browser won't let me do that delete.  It says "Sorry, could not change the permissions of "XXXX": Operation not supported by backend."
Thanks in advance for the help.

```
gksudo nautilus
``` Then you can delete it.

---

### Post by JonWhite on 2009-02-10
> **dcstar said:**
> ```
gksudo nautilus
``` Then you can delete it.
Dave, thanks.
Please pardon my ignorance, but when and where do I enter the code you provided?
Extreme Ubuntu novice here.
Ta.

---

### Post by not a pipe on 2009-02-10
Applications>>>Accessories>>>Terminal
And you may want to drag the terminal icon to the top panel or hotkey it so you can get to it easily as it comes in handy sometimes.

---

### Post by Slim Odds on 2009-02-10
> **JonWhite said:**
> Dave, thanks.
Please pardon my ignorance, but when and where do I enter the code you provided?
Extreme Ubuntu novice here.
Ta.

Alt-F2

---

### Post by JonWhite on 2009-02-10
> **Slim Odds said:**
> Alt-F2

That did the trick.
Thanks much.

---

