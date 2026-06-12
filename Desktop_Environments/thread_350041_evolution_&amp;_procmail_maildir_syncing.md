---
title: "evolution &amp; procmail maildir syncing"
date: 2007-01-31
forum: Desktop Environments
---

### Post by engineer on 2007-01-31
i configured evolution, to use a maildir backend.
the maildir is filled by fetchmail/procmail.
from time to time, depending on the mail check intervals, i get an error.
evolution tells, it can't sync the mailboxes because it couldn't get a lock because there are too many files.

for me the reason is more or less clear. but how can i prevent these errors?

ps: i'll try to post the correct error message. everytime the same, when looking for the correct error text, the error simply doesn't appear...

---

### Post by engineer on 2007-01-31
here is the error message:

```

Error while Synchronising "Inbox".

Could not create lock file for /home/hermann/.evolution/mail/local/Inbox: Too many open files

```

---

