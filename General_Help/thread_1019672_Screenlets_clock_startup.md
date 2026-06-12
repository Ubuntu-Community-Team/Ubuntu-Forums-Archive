---
title: "Screenlets clock startup"
date: 2008-12-23
forum: General Help
---

### Post by davidself1001 on 2008-12-23
When I shut down my system I get a message that screenlets disk guage and clock cannot be auto restarted.  Both are in my startup session.  When I restart the disk guage comes up but the clock does not.  How can I get the clock to start auto on restart?

---

### Post by Wartender on 2008-12-23
in the screenlets manager, have you checked the "auto start on login box?"

---

### Post by davidself1001 on 2008-12-23
Yes.  forgot to mention that.

---

### Post by xunilevol on 2008-12-24
try this,when you open screenlets,make sure your open on start up is checkmarked. right click on your clock,select window/widget. shut down screenlets, restart ctrl+alt+backspace and you should be good to go. also check in ccsm that you have widgets checkmarked.
hope that helps,it worked for me

---

### Post by davidself1001 on 2008-12-24
Did not work.  One thing that is odd and may be a problem is that when I look under preference->Sessions->Current Session the Clock screenlet is not shown even though it is on my screen.  The Disk Usage screenlet is in the current list and is also showing on my desktop.  I also checked in my ~/.gnome2/session file and the clock is not saved as a restart program there either even though it is listed as a startup program in Preference->Sessions.  It's a bit odd.

---

### Post by davidself1001 on 2008-12-26
bump

---

