---
title: "Google Browser Sync extension works only on Firefox run as root"
date: 2006-10-10
forum: Desktop Environments
---

### Post by Sebhelyesfarku on 2006-10-10
As normal user (although with admin rights) the extension is installed but doesn't do the first synchronisation on the browser restart, the Settings and Reconnect menus are broken. With 'sudo firefox', the extension does the first sync properly for the root? Any ideas?

---

### Post by ketanpadegaonkar on 2006-10-11
Yes,
This works on ubuntu firefox only when run as root. I do not know if this is a problem with other distros as well.

---

### Post by mozetti on 2006-10-11
Not here -- Google browser sync works for me without sudo/gksu. 

Maybe a problem related to how you installed Ffx or the extension?

---

### Post by Sebhelyesfarku on 2006-10-11
> **mozetti said:**
> Not here -- Google browser sync works for me without sudo/gksu. 
Maybe a problem related to how you installed Ffx or the extension?

Thanks for the replies...

Firefox has been installed with the standard Ubuntu install from the Live CD, later got updated with the standard update. Now it's:

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.0.7) Gecko/20060921 Ubuntu/dapper-security Firefox/1.5.0.7

All the extensions were installed as normal user, they work except the Google Browser Sync...

Btw, after installing Browser Sync as normal user and restarting Firefox, the browser doesn't start, nothing happens. On the second restart the browser works but the Browser Sync extension is broken. At the first restart the extension should connect to Google, ask for Account name password etc. but it doesn't happen.

Btw #2, the system runs on VMplayer on Win XP as host but I guess it shouldn't matter...

---

