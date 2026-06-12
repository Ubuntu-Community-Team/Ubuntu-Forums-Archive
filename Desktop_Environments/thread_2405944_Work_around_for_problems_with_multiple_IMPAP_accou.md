---
title: "Work around for problems with multiple IMPAP accounts on Evolution 3.30.1-1build1"
date: 2018-11-13
forum: Desktop Environments
---

### Post by cigtoxdoc on 2018-11-13
Evolution 3.30.1-1build1 has a problem when you are upgrading from previous versions of Evolution on Ubuntu OS.  If you try to add a second IMAP account, Evolution "locks up".

After much discussions with the experts at [email]evolution-list@gnome.org[/email], one of them discovered the problem.  This problem may be caused by errors in the  ~/.cache/evoluton/mail/<account-uid>/ files.  The solution is to close Evolution use Nemo or similar file manager in the super user mode (sudo nemo), and delete the files.  They are in your home directory under .cache.

John

---

