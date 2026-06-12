---
title: "Evolution copying message to Trash on moving - how to prevent?"
date: 2006-09-27
forum: Desktop Environments
---

### Post by eudoxos on 2006-09-27
Hi, every time I move a message from the Inbox to any other folder on the IMAP server, Evolution (2.6.1, dapper) creates a copy of that message in Trash. Is there a way to prevent this?

Alternatively, is it possible to configure Evolution to move messages marked manually as spam to an arbitrary folder (without making that copy to Trash, again)?

Thanks, Eudoxos

---

### Post by dcstar on 2006-09-27
> **eudoxos said:**
> Hi, every time I move a message from the Inbox to any other folder on the IMAP server, Evolution (2.6.1, dapper) creates a copy of that message in Trash. Is there a way to prevent this?

Alternatively, is it possible to configure Evolution to move messages marked manually as spam to an arbitrary folder (without making that copy to Trash, again)?

Thanks, Eudoxos

I seem to remember putting something like this in as a bug a while back, and the answer I received is that it was a design "feature" as a "Move" is actually performed as a Copy and then a Delete in Evolution - so there always is something in the Trash folder.

I have an Evolution Message Filter to process any messages with Spam in the subject which marks them as Read, sets the status as Junk, and then deletes them.

---

### Post by eudoxos on 2006-09-27
Thanks. But I have spam moved to the respective folder on the server side, I want to move those false negatives to spam without tainting my trash folder by spam. Well, maybe I file a bug or switch to thunderbird, which seems more extensible anyway.

But I appreciate other replies how to prevent it, or even a justification of the design "copy on move".

---

