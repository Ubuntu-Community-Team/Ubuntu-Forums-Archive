---
title: "openoffice 2.4 won't open unless as root"
date: 2008-05-02
forum: Desktop Environments
---

### Post by berg1976 on 2008-05-02
If I try to open any openoffice application as a 'normal' user, the following message appears:

[Java framework] Error in function createSettingsDocument (elements.cxx).javaldx failed! 
[Java framework] Error in function createSettingsDocument (elements.cxx).

 (if opened in terminal)

or

the application cannot be started. The language of the user interface cannot be determined

(through menu and terminal)

It works fine when typing 'sudo openoffice' or when opening a file through a root-file manager.

re-install did not bring any change.

Any help appreciated!

---

### Post by Hagar Delest on 2008-05-03
Try to rename your OOo user profile (~/.openoffice.org2), OOo will create a new one.

---

### Post by berg1976 on 2008-05-03
Excellent advise
Cheers mate!!!

---

### Post by WendyWeber on 2008-05-31
I'm having a similar problem. After a reinstall of Evolution that caused some problems with Open Office, my Open Office 2.4 won't start from the gnome menu or by clicking an oo file. It does start when I start swriter from a prompt, not begin root. I have deleted my user profile, with no effect. Anything else I can try? Thanks in advance.

---

### Post by Pandyman on 2008-06-19
Same as above.  Evolution changed (I guess from an update) recently so I can not view the list of recent messages and the selected one on the same page.  I'm now back with Thunderbird (haven't used since windows days).  I decided to remove Evolution and now I can't start open office.  Thanks for the tip "sudo openoffice" at least I'm in business.  I can't believe OO doesn't have all its own dependences.

---

### Post by Pandyman on 2008-07-03
Today's updates has included a fix so that Open Office starts and works fine.  Thanks guys.

---

### Post by bobromeo on 2008-09-24
> **Pandyman said:**
> Today's updates has included a fix so that Open Office starts and works fine.  Thanks guys.
I still had this problem today.
My pofile was locked and owned by root !?!
- renamed profile
- ooffice -writer %U
--> /home/bobromeo/%U does not exist
- ooffice -writer
--> works fine

Recap:
- see if you own your profile
- lose the %U parameter with ooffice commands and in menus
<-- This problem only occurs when teh 'supervisor' is using ooffice.

---

### Post by bobromeo on 2008-09-24
When I log in as another user I don't have these problems.
Even the %U in the menus is not a problem ?!?

---

