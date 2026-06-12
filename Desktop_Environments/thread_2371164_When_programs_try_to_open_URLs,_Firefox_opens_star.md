---
title: "When programs try to open URLs, Firefox opens start page only."
date: 2017-09-11
forum: Desktop Environments
---

### Post by Dave Harmon on 2017-09-11
I can browse pages normally within Firefox, and I can load pages with "firefox *<url>*", both without incident.

But when any *other* program, including Thunderbird, tries to open a URL, Firefox responds by opening a new window with the start page.  There is no sign in Firefox of what URL they might have been trying to open.  

This has been happening for a long time (since I was using 14.04 LTS), but it's currently a showstopper with another program that seems to have switched to using a browser URL for signin.

---

### Post by mc4man on 2017-09-12
All that works ok here in 16.04
Maybe try a new profile. To do that without losing current (default) one - 
With firefox** not** running, in a terminal
```
firefox -profilemanager
```
In the popup "create" a new profile, name it anything but default.
Leave the check mark as in screen, then click on the start firefox button (- you must do this to switch profiles.
Then close firefox, try to open a url thru an app.

To switch back just do above again, this time choose the default profile & click the start firefox button... ( or simply delete the new profile..

---

