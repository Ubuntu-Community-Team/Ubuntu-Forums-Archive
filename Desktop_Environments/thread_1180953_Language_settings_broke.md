---
title: "Language settings broke"
date: 2009-06-07
forum: Desktop Environments
---

### Post by GNUbee40 on 2009-06-07
Hi there!

I am running Ubuntu with EN(DK) which means english setting for Denmark. However, it is quite annoying that the Date and time format does not follow Danish locale settings which means day-month-year. Instead, it is reverse, which makes it complicated using some programs relying on system settings for formatting dates.
There seems to be no setting for customizing this via the GUI. You'll have to change the whole Language back to DK for getting the right Date format. 
I tried to modify the Locale settings on the command line.
I edited 
[LIST]
[*]/etc/evironment
[*]/etc/default/locale
[*]/var/lib/locales/supported.d/local
[/LIST]
and added lines to modify Time and Date format. I even made a custom UTF-8 file. However, month and day continue to show in reverse order. I thus deleted my edits (could not find the custom UTF-8 file though), and proceeded to change the whole language in System->Settings->Language Settings. 
But now the GUI for language settings keeps crashing, and thus I seem stuck with the english settings. 
Is there anyone who can help me figure out, what might cause this behaviour?

Regards

---

