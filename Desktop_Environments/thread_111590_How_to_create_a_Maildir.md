---
title: "How to create a Maildir?"
date: 2006-01-02
forum: Desktop Environments
---

### Post by rosslaird on 2006-01-02
This is driving me crazy:

I'm trying to sync my remote IMAP emails with my local machine (as a backup repository of my emails) using fetchmail, getmail, or isync. Fetchmail seems to be unable to download the messages without also removing them from the server, which I do not want, and getmail/isync always fail with the message that my destination folder is not a Maildir. I have tried various things to create this maildir (including using the folder that fetchmail created), to no avail. I have looked on google until my eyes are itchy. I have read about something called MakeMaildir, which I do not have and cannot find in the repositories.

Help would be appreciated. Even a useful link.

Ross

---

### Post by gnottage on 2006-01-13
The command is maildirmake. Go to your home directory *cd ~*, and then type *maildirmake .maildir*

Let us know if that works...

---

### Post by rosslaird on 2006-01-13
[QUOTE=gnottage]The command is maildirmake. Go to your home directory *cd ~*, and then type *maildirmake .maildir*
[/QUOTE]

"Command not found"

---

