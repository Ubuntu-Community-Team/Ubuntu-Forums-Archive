---
title: "Problem synchronizing Google calendar with opensync"
date: 2009-03-19
forum: General Help
---

### Post by wwnliu on 2009-03-19
Hi,

I am trying to use opensync to sync my phone(a SE W-series phone), Evolution and Google Calendar. Opensync do work between Evolution and my phone. But Whenever I try to access Google Calendar it returns the following messages.

```
~$ msynctool --sync GoogleCal-Phone
Synchronizing group "GoogleCal-Phone" 
The previous synchronization was unclean. Slow-syncing
Member 1 of type google-calendar just connected
Member 2 of type irmc-sync just connected
All clients connected or error 
Member 1 of type google-calendar had an error while getting changes: Error reading xml data from helper
Member 1 of type google-calendar just disconnected
Member 2 of type irmc-sync just sent all changes
Member 2 of type irmc-sync just disconnected
All clients have disconnected
The sync failed: Unable to read from one of the members
Error while synchronizing: Unable to read from one of the members

```

Any idea what causes the error? (p.s. my google account doesn't end with @google.com, I am not sure would it has any effect)

---

