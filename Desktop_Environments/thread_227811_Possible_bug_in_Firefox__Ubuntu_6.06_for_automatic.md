---
title: "Possible bug in Firefox / Ubuntu 6.06 for automatic updates"
date: 2006-08-02
forum: Desktop Environments
---

### Post by slakkie on 2006-08-02
Hello to all,

I want to file a bug report, but I'm unsure wheter this problem only excists on Ubuntu, or on other systems as well - should I create a bugreport at Ubuntu or at Mozilla?

I'm able to reproduce the bug on different systems (all running Ubuntu 6.06). Firefox has been installed from the reposities (default Ubuntu desktop install).

Firefox details:
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.0.5) Gecko/20060727 Ubuntu/dapper-security Firefox/1.5.0.5

Machine details:
Linux sinti 2.6.15-25-386 #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006 i686 GNU/Linux

Problem:

Once you set automatic updates, you cannot deselect it, and all the automatic update options are greyed out. (See attachement).

Howto reproduce the problem:
* Goto preferences
* Advanced
* Update tab
* Select the "Automaticly download and... "

At this point, all the options for updating firefox become grey. And there is no turning back.

I've tried to undo the action, via about:config

app.update.auto is set to 'true', change to 'false' will set the option "Ask me what to do" in the update preferences.

app.update.enabled is in status *locked* and the boolean is set to false.

I'm unable to change this app.update.enabled, and don't know how to get it unlocked..

---

### Post by etank on 2006-08-02
I just tried the same thing on my test machine and I got the same results that you did.

---

### Post by Epperly on 2006-08-02
Mine is grayed out to begin with (but at ask me what I want to do), I usually just update along with the system though.

---

