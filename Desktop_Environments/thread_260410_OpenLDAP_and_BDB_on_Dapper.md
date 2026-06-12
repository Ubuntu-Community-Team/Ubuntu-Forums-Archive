---
title: "OpenLDAP and BDB on Dapper"
date: 2006-09-18
forum: Desktop Environments
---

### Post by eriktown on 2006-09-18
I'm trying to set up OpenLDAP on Dapper, and it doesn't seem to understand Berkeley DB:

(a whole bunch of stuff as slapd.conf is processed snipped)
line 74 (database bdb)
Unrecognized database type (bdb)
database bdb initialization failed.
slapd shutdown: freeing system resources.
slapd stopped.
connections_destroy: nothing to destroy.

Anyone have any idea how I can fix this? There doesn't seem to be a separate bdb package...

---

