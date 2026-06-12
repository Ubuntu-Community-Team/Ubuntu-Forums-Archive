---
title: "cups-pdf works for one user, not for another"
date: 2011-07-20
forum: Desktop Environments
---

### Post by henrylaw on 2011-07-20
There are two user accounts on my Ubuntu Lucid desktop system.  One (mine) can print to a PDF via cups-pdf (version 2.5.0-12); the other (my wife's) cannot.  

When I try from her account no PDF is created and /var/log/cups/cups-pdf_log contains the dreaded "[ERROR] failed to set file mode for PDF file (non fatal)" message.

These are both normal user accounts[INDENT][FONT=Fixedsys]henry:x:1000:1000:henry,,,:/home/henry:/bin/bash
hername:x:1001:100:Hername,,,,:/d/u/Foo:/bin/bash[/FONT]
[/INDENT]Her account is a member of all the groups that mine is a member of (and some others, in fact).  The only obvious differences between the two is that her home directory isn't /home/hername but in a different file system (see above), and her primary group is one called "users" (100), of which I am also a member.  A directory called PDF exists in her home directory.[INDENT]drwxrwxr-x 2 hername users 4096 2011-07-20 15:35 /d/u/Foo/PDF
[/INDENT]The cups configuration contains 'Out ${HOME}/PDF' (and in any case it works for me), and and apparmor configuration for cups contains '@{HOME}/PDF/ rw,' (ditto).

The backend has what I believe to be the right permissions (and in any case ... it works for me)[INDENT]-rwx------ 1 root root 27072 2009-11-30 20:21 /usr/lib/cups/backend/cups-pdf
[/INDENT]This looks like some obscure permissions/group membership problem but I've exhausted all the things I can think of to try.  Can someone suggest where to look next?

I don't need to tell you the earache I'm getting over this ...

---

