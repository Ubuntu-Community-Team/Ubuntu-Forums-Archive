---
title: "Missed Evolution Calendar Alarms"
date: 2005-10-18
forum: Desktop Environments
---

### Post by idegen on 2005-10-18
Since upgrading to Breezy, Evolution no longer displays missed calendar alarms when it starts.  Is there any way to reenable this?

Thanks!

Greg

---

### Post by Kokanee on 2005-10-18
Make sure the **evolution-alarm-notify** process is running in the background.  I *think* that you need to install the **evolution-data-server** package for this?

---

### Post by dcstar on 2005-11-01
[QUOTE=idegen]Since upgrading to Breezy, Evolution no longer displays missed calendar alarms when it starts.  Is there any way to reenable this?

Thanks!

Greg[/QUOTE]
This has happened on my system to, the evolution-alarm-notify process is running so this is a definite problem.

Edit: It seems that this is a known problem:
[http://bugzilla.gnome.org/show_bug.cgi?id=319217](http://bugzilla.gnome.org/show_bug.cgi?id=319217)

---

