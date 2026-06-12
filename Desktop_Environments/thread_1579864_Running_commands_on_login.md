---
title: "Running commands on login"
date: 2010-09-22
forum: Desktop Environments
---

### Post by tnsmart on 2010-09-22
I have been trying to figure out how to automatically run terminal commands on login.  For example, I want to run Firefox on login.  When I run 'firefox' in terminal, it opens.  This is what I tried:
I went to System > Preference > Startup Applications and clicked on 'Add'.  I gave it a name, typed 'firefox' into the command field and left the comment blank and added it to the list, making sure that the box was checked.  

However, it does not work on startup; nothing happens.  I have also tried this with other commands.  Any ideas how to get this to work?  Thanks.

---

### Post by Brandon Williams on 2010-09-22
What you described sounds right. Are there any messages in ~/.xsession-errors after you log in that indicate some problem with the startup sequence for firefox?

---

