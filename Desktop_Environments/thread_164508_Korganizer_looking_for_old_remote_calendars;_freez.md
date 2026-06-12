---
title: "Korganizer looking for old remote calendars; freezes"
date: 2006-04-22
forum: Desktop Environments
---

### Post by argotnaut on 2006-04-22
I had problems using remote calendars with Korganizer, and couldn't get it to start or stay open long enough to delete them. So I deleted the folder ~./kde/share/apps/korganizer/ . This deleted the local calendar, but Korganizer is still looking for the remote calendars.

When I open it in a terminal, I get a line like this for each of the remote calendars:

```
libkcal: ERROR: Can't read uid map file 'home/argotnaut/.kde/share/apps/kcal/uidmaps/remote_sgrVk5IQvX'
```

How can I get it to stop looking for these calendars?

---

