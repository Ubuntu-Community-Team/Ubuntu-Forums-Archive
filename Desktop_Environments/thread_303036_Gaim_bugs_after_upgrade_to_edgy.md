---
title: "Gaim bugs after upgrade to edgy"
date: 2006-11-19
forum: Desktop Environments
---

### Post by tinker123 on 2006-11-19
Hi;

A few weird things happed to my copy of gaim after I upgraded to edgy from dapper.  Can anyone tell me how to fix them?:


1. The system tray icon is a picture of the "gaim-man" with a sticky note on him, even though I am not away or idle.

2. The sound effects don't come on, even though they do when I press the "test" button in the preferences menu.  In preferences | sound what does the choice "sound method" mean and what do I want?

3. When I start Gaim it does not show me my buddy list on start up.


Thanks in advance!

---

### Post by tinker123 on 2006-11-23
This fixed itself after I fixed a buggy sources.list and did a dist-upgrade.

---

### Post by selfrisingflour on 2007-01-08
What did you need to change on your sources.list?  I need to do the dist upgrade.

---

### Post by userundefine on 2007-01-08
> **tinker123 said:**
> 2. The sound effects don't come on, even though they do when I press the "test" button in the preferences menu.  In preferences | sound what does the choice "sound method" mean and what do I want?

I had this problem in the same situation.  I fixed it by removing the .gaim directory in my /home.

---

