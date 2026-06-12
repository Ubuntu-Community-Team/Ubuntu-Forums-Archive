---
title: "[SOLVED] Setting up Evolution With Mail Download With fetchmail"
date: 2008-02-21
forum: Desktop Environments
---

### Post by cmnorton on 2008-02-21
Synching Evolution with our new IMAP server is problematic, so I'd like to run fetchmail in a cron job, and then have Evolution grab its mail out of /var/spool/mail/username.

I've tried different flavors of this (different settings that appear to look like they'd point to /var/spool/mail), and keep getting errors from Evolution. These errors are basically in two flavors, either permissions based -- I've looked and the permissions are fine -- or that I'm asking to open a directory, not a file.

If I want Evolution to open mail in /var/spool/mail/username, what are the settings to use?

Many thanks.
cmn

Edits: 2/22/2008

Instead of local delivery, using Standard Unix mbox spool file" will allow the user's mbox file to be selected in /var/mail.

---

