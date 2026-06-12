---
title: "How to make Emerald default?"
date: 2008-06-01
forum: Desktop Environments
---

### Post by WBL on 2008-06-01
I'm running GNOME + Compiz.  I just installed Emerald.  However, it does not run once I start up - gtk-window-decorator does.

How do I make it run Emerald instead of gtk-window-decorator?

-WBL

---

### Post by benerivo on 2008-06-01
Go to Main Menu>System>Preferences>Sessions and make a new startup program. Call it emerald and the executable is just called

emerald

Then logout and log back in.
 If this doesn't work, then install compiz settings manager (i forget the actual package name) and in one of the options windows, it asks you about what the default window decorator should be. Change it from /usr/bin/whateveritsays to /usr/bin/emerald

---

### Post by nilarimogard on 2008-06-01
i use a script.sh that i made run at startup:

#!/bin/bash
sleep 10 && emerald --replace ;

(don't forget to make it executable)

---

### Post by gareth_005 on 2008-06-01
"Preferences"->"Advanced desktop effects"->"Effects"->"Window decoration".
Set "Command" to "emerald --replace"

---

### Post by WBL on 2008-06-01
> **gareth_005 said:**
> "Preferences"->"Advanced desktop effects"->"Effects"->"Window decoration".
Set "Command" to "emerald --replace"


Thanks, man - that did the trick.  :)

-WBL

---

### Post by bajun on 2008-07-18
Or better change following line in /usr/bin/compiz-decorator:
```
USE_EMERALD="no"
```
and set this to 
```
USE_EMERALD="yes"
```,
then there are fallback options, for example "Do not leave users without decoration if decorator fails".

---

### Post by davidryder on 2009-03-05
> **bajun said:**
> Or better change following line in /usr/bin/compiz-decorator:
```
USE_EMERALD="no"
```
and set this to 
```
USE_EMERALD="yes"
```,
then there are fallback options, for example "Do not leave users without decoration if decorator fails".

I like this solution :D

---

### Post by hemebond on 2009-03-27
The proper way to do this is to create or edit the file ~/.compiz/compiz-manager to have the line```
USE_EMERALD="yes"
```This file is read by Compiz Fusion and over-rides the default settings in /usr/bin/compiz-decorator.

---

### Post by Pelsia on 2009-10-21
Don't mean to zombie a thread, instead share a solution to this same problem (under slightly different circumstances).  When trying to make emerald my default kept getting the following errors in the terminal:

/usr/share/themes/Clearlooks/gtk-2.0/gtkrc:49: Invalid symbolic color 'bg_color'
/usr/share/themes/Clearlooks/gtk-2.0/gtkrc:49: error: invalid identifier `bg_color', expected valid identifier

[FONT=Verdana]I didn't have the advanced desktop settings in my system preferences, but was able to resolve 
it via the compiz-fusion icon.  And from there setting the default desktop manager to 
emerald.  In searching these messages seem to stem from an unresolved bug, whether
that is the case or not doing the above with the compiz icon resolves it.
[/FONT]

---

