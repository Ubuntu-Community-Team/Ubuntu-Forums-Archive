---
title: "Evolution failing to start after crash"
date: 2007-11-15
forum: Desktop Environments
---

### Post by pinkunicorn on 2007-11-15
When I got home today, my Gutsy machine had crashed (black screen, caps lock and another diode on the keyboard slowly flashing). That's bad, but beside the point right now. After rebooting, I tried to start Evolution.

The window comes up, along with an error dialog (translated from Swedish):

```
Error when opening store imap://unicorn;auth=CRAM-MD5@imap.lysator.liu.se/;imap_custom_headers;command=ssh%20-C%20-l%20%25u%20%25h%20exec%20/usr/sbin/imapd;use_ssl=always;use_lsub;filter.

Couldn't create directory /home/hans/.evolution/mail/imap/unicorn@imap.lysator.liu.se: Not a directory
```

This is what I find among my files:```
hans@owl ~ :-) cd .evolution/
hans@owl ~/.evolution :-) ls -l mail
-rw------- 1 hans hans 60653568 2007-11-15 03:25 mail
hans@owl ~/.evolution :-) file mail
mail: SQLite 3.x database
```

What happened, and more importantly, how do I fix it?

---

