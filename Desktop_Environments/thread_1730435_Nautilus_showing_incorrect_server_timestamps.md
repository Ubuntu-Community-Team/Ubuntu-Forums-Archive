---
title: "Nautilus showing incorrect server timestamps"
date: 2011-04-16
forum: Desktop Environments
---

### Post by purvez on 2011-04-16
I have a nautilus timestamp problem as follows;

I am based in London and so currently have bst (GMT+1).

When I connect to my production server using ftp and then use nautilus to view the mounted ftp, all timestamps in nautilus are 1 hour ahead of where they should be.

I've checked the time on the production server and the timezone and they are both correct.  If I ssh to the server and view the timestamps there then they show correctly.

Timestamps displayed from my own desktop also show correctly in nautilus.

It's almost like nautilus does not recognise that the time  on the server is already bst adjusted and therefore adds an hour to it.

Please can anybody tell me what I need to do to correct this behaviour.

Thanks

Purvez

---

