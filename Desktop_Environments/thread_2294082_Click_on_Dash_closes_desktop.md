---
title: "Click on Dash closes desktop"
date: 2015-09-09
forum: Desktop Environments
---

### Post by WMarkTHarrison on 2015-09-09
When I click on the Dash icon, or press the 'Windows' key (sorry)  the desktop closes and I have to log in again.
After logging in again, all applications have closed.  
In some cases everything unsaved is lost - e.g. LibreOffice, though it usually recovers the unsaved docs successfully.  
In Thunderbird unsaved emails are there in Drafts.

The only way to find applications which are not in the sidebar is to use the file manager to get to the applications folder and start them from there.

I am using 32-bit 14.04 on an elderly P4 with 2.5GB of memory and Intel on-board 915G graphics.

Any ideas?

---

### Post by CantankRus on 2015-09-09
Try resetting compiz/unity to default.
```
dconf reset -f /org/compiz/
```
After running the above command, logout and back in.

*****NOTE**: You will have to redo any customizations you may have made to compiz/unity
like launcher icon size.

---

### Post by WMarkTHarrison on 2015-09-13
Thank you.  I tried your suggestion but no change.

Another thing - it only happens when I'm logged in as myself..  It doesn't do it if I log in as Guest.  There are no other users

---

