---
title: "Evolution won't present new inbox subfolders"
date: 2011-01-05
forum: Desktop Environments
---

### Post by Skaperen on 2011-01-05
When a new subfolder is created under the inbox on the mail server (by whatever conditions will create one), Evolution does not appear to pick up on it, or at least does not present it to the user.  This happens even if Evolution quits and is restarted.

1.  While stracing the IMAP worker process for the user with a new subfolder, the IMAP worker does access every message in the new subfolder.  It is not know if this is done because it always does this, or because Evolution requested this.  In my case, Dovecot is the IMAP server software.

2.  If the directory tree "~/.evolution/mail/imap" is deleted while Evolution is not running, and Evolution is afterwards restarted, then it will pick up on new subfolders.  So it appears Evolution is keeping negative cache ... e.g. "I know that isn't there, so I'll pretend it's not there, even though it really is there".  It takes several minutes to re-acquire all the info from the mail server.

Clearly, we expect mail clients to detect new MAIL when it shows up.  Why can't it do so for a subfolder?

---

