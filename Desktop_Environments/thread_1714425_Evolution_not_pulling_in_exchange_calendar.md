---
title: "Evolution not pulling in exchange calendar"
date: 2011-03-25
forum: Desktop Environments
---

### Post by retrodans on 2011-03-25
I have just setup evolution to pull in my exchange emails using MAPI.  All seems to be well, except that it isn't pulling down my calendar or tasks.  I understood that it was supposed to automatically do this, is this correct?

We are using exchange 2005 I believe, so wonder if this is specifically the issue.

Thankyou for any recommendations you can give in debugging this.
Dan

---

### Post by sdredwingsfan on 2011-05-30
I'm not sure if you're running 11.04 like me but I had to close evolution, kill the e-addressbook-factory & e-calendar-factory process.  I restarted evolution went to calendar & it started populating entries.  Afterwards, I went into contacts & it prompted me for GAL authentication & it worked too. We're on exchange 2007 too btw.  HTH

---

