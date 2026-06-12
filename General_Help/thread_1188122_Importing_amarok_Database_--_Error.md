---
title: "Importing amarok Database -- Error"
date: 2009-06-15
forum: General Help
---

### Post by jenkinbr on 2009-06-15
Did a bit of searching on this and didn't find much.

I am getting an error when trying to import my old Amarok 1.4 database into Amarok2.  Here's what I did:

[list=1]
[*]Delete ~/.kde/share/apps/amarok
[*]Open Amarok
[*]Update Collection (This happened automatically)
[*]Open 'Settings' >> 'Confiure Amarok...'
[*]Go to Collection tab
[*]Click on 'Import Collection'
[*]Chose 'Amarok 1.4' and click 'next'
[*]Edit the path from /home/jenkinbr/.kde/share/apps/amarok/collection.db to /home/jenkinbr/.kde/share/apps/amarok1/collection.db (the latter is where amarok1.4 settings were stored, the former doesn't exist because amarok2 uses it's own implimentation of MySQL and doesn't use sqlite
[*]Click next
[*]become baffeled by the error that is spit out: ```
Error: Could not open Amarok 1.4 database: Driver not loaded Driver not loaded
Failed: Unable to import statistics
```
[*]Click finish. Click close
[*]post here to see if anyone else has this issue.
[/list]

Any ideas???

Nevermind -- 
[sudo apt-get update && sudo apt-get upgrade && sudo apt--get install libqt4-sql* did the trick.  I was missing libqt4-sql-sqlite

---

