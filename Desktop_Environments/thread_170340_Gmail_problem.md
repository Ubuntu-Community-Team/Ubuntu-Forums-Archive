---
title: "Gmail problem"
date: 2006-05-04
forum: Desktop Environments
---

### Post by dogeatery on 2006-05-04
When I'm in Gmail Firefox always loads it in basic HTML.  When I click to switch to regular view it just reloads to basic HTML.:confused:   Is there something I need to tweak in my firefox settings to make this work?  I am running firefox 1.5

---

### Post by neouser99 on 2006-05-04
clear your cookies and cache? if that doesn't work i would assume that it isn't a problem with your install rather a problem with gmail, and you should get back to them. i have never seen this before, so i am just shooting in the dark.

-neo

---

### Post by dogeatery on 2006-05-04
yeah, I have tried clearing cookies/cache and it still doesn't work.  I'm curious if anyone else has encountered this in firefox but I guess I'll have to try getting in touch with the gmail peeps.

---

### Post by matthewstory on 2006-05-04
Make sure that javascript is enabled before you do anything rash:

open firefox:

Edit > Preference > Web Options > Enable Javascript

check that box, it should be checked by default but who knows.

---

### Post by louis_nichols on 2006-05-04
Also, make sure java is installed and configured. In the address bar type ```
about:plugins
``` and see if it says anything about java.

---

### Post by dogeatery on 2007-06-19
Went through and found this unresolved thread which I started:

The problem was Firefox User Agent Switcher add-on.  All I had to do was switch it off of default and then tell Gmail to give me 'standard view' and it works fine.  Basically, just switch the user-agent and Gmail should work like normal.  This one drove me crazy for a while!

-dogeatery

---

