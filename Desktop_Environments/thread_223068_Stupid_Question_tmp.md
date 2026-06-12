---
title: "Stupid Question? /tmp"
date: 2006-07-25
forum: Desktop Environments
---

### Post by Hi-Teck on 2006-07-25
Is /tmp where net vids and pics are stored when you decided to just view the images instead of saving things to a location?

Also does  /tmp clear itself after a awhile you do u have to clean it every so often?

---

### Post by simonn on 2006-07-25
> **Hi-Teck said:**
> Is /tmp where net vids and pics are stored when you decided to just view the images instead of saving things to a location?


Usually yes, but it depends on the software.

> Also does  /tmp clear itself after a awhile you do u have to clean it every so often?

This is down to the individual applications which use /tmp. They should tidy up after using it. If you ctrl+c an application then it will not be able to clean up.

By default, Ubuntu cleans up /tmp on boot.

Not a good idea to just delete stuff from it. It could potential cause serious problems.

---

### Post by chalex on 2006-07-25
On my machine (default Dapper), Firefox deletes its files in /tmp when it exits.  This is the typical behaviour for most applications.

---

