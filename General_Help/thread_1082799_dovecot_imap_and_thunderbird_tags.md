---
title: "dovecot imap and thunderbird tags"
date: 2009-02-28
forum: General Help
---

### Post by lorebett on 2009-02-28
We've been using an imap(s) dovecot server for a while on an ubuntu 8.04.2 and we noted that tags set by thunderbird ("important", "to do", etc.) are almost always lost, i.e., when connecting to the same imap account from another machine, the tags are not there anymore...  this always happens for the Inbox, and seldomly for other imap folders... anyone else experiencing this?

---

### Post by lorebett on 2009-03-22
> **lorebett said:**
> We've been using an imap(s) dovecot server for a while on an ubuntu 8.04.2 and we noted that tags set by thunderbird ("important", "to do", etc.) are almost always lost, i.e., when connecting to the same imap account from another machine, the tags are not there anymore...  this always happens for the Inbox, and seldomly for other imap folders... anyone else experiencing this?

by the way, this was solved by setting the caching off in the dovecot configuration file :popcorn:

---

### Post by lorebett on 2010-07-11
and to be more specific I set

```
mbox_lazy_writes = no
```

---

### Post by ElGatoFlojo on 2010-07-28
Thanks! I've been looking for this :)

---

