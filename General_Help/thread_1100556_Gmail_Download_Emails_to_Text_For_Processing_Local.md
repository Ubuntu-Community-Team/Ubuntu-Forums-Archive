---
title: "Gmail: Download Emails to Text For Processing Locally"
date: 2009-03-19
forum: General Help
---

### Post by mastermindg on 2009-03-19
I have an external application that emails my GMail account regularly with program updates. What I would like to do is to setup a script to act upon these updates. Is there a way to download email (in particular from GMail) to text files for processing by a cron/script?

---

### Post by kryptikos on 2009-03-19
Gmail allows you to set up a pop method to download your messages [http://mail.google.com/support/bin/answer.py?hl=en&answer=13273]("http://mail.google.com/support/bin/answer.py?hl=en&answer=13273"). 

You could set up the pop with alpine [http://www.washington.edu/alpine/]("http://www.washington.edu/alpine/")or some other text based console email client and run your cron against the messages there. You can install alpine with aptitude or apt-get...it's in the repositories.

---

### Post by mastermindg on 2009-03-19
I figured out that the easiest way to do this is to use offlineimap. It syncs messages using IMAP to local folders.

---

### Post by lovinglinux on 2009-03-19
> **mastermindg said:**
> I figured out that the easiest way to do this is to use offlineimap. It syncs messages using IMAP to local folders.

Yep, offlineimap is great. Take a look on [this thread]("http://ubuntuforums.org/showthread.php?t=1099951") for an example of extracting attachments.

---

### Post by cros13 on 2009-03-19
Conduit is a pretty good option too.

---

