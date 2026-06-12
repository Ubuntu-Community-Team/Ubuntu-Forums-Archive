---
title: "Evolution forgets folder view"
date: 2009-02-25
forum: General Help
---

### Post by dclement on 2009-02-25
Hello,

After my computer froze today, I am facing the following problem with Evolution: every time I restart the program, all the mail folders are closed (inside "On this computer"). I have to open them manually.

I haven't lost any mail in the process, but I'd like to restore the normal behavior, that is, find my mail folders as I left them.

How can I do that? TIA, Daniel

---

### Post by sahabcse on 2009-02-25
Hi 

For backup and restore the evolution follow the below url

======================================
[http://sahabm.blogspot.com/2009/02/evolution-backup-and-restore-ubuntu.html](http://sahabm.blogspot.com/2009/02/evolution-backup-and-restore-ubuntu.html)
--------------------------------------

Regards,
Sahab

---

### Post by dclement on 2009-02-25
Hello,

Thanks for the reply. Still, it does not seem to do what I want. No matter how I do the backup (your instructions, or Evolution's builtin backup/restore), I end up with the folders view always resetting itself.

I'm afraid that whatever went wrong gets "backed up" with the rest.

Also (not sure if it matters) I got a couple of errors trying to follow your web page:

- I have no  .gnome2_private/Evolution directory;

- and the line:  gconftool-2 --(un)load evolution_setting.xml
gave me an error "failed to open evolution_setting.xml: no such file or directory"

Perhaps _this_ is part of my problem?

Regards, Daniel

---

### Post by sahabcse on 2009-02-25
Hi

No issue. I have eliminate those steps and check it out, now every thing works fine,

Thanks and regards
Sahab

---

### Post by Ericyzfr1 on 2009-02-25
I remember I had a similar issue, it disappeared when I manually exported my local mailbox and imported the different mbox files. The same way if you would migrate from Thunderbird, you might also need to recreate the local folders.

---

### Post by dclement on 2009-02-26
Thanks to you both for your replies. Here are the news:

Sahab: your modified backup/restore method works fine, but I could try it on another hard drive with a brand new Evolution setup: the imported backup showed the same problem as the other. So I'm bound to think something went wrong in the /.evolution folder, thus propagating to the backups.

Ericyzfr1: how can you "manually export" from Evolution? What did the trick for me was to extract the various folders and mail files (archived as per Sahab's method), one by one, to a newly created /.evolution folder. Is that what you meant?

However, I was able to recover everything but the mail filtering rules. Had to recreate them by hand.

So... should I mark this thread "solved"? The whole process seemed pretty tedious to me; there has to be a smarter way...

Thanks again - Regards, Daniel

---

