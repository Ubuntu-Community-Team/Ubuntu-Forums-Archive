---
title: "Keeping UIDs in sync"
date: 2005-01-07
forum: General Help
---

### Post by nocturn on 2005-01-07
I have several workstations and one server at home.

I would like to keep UID's consistent over the workstations without completely depending on the server (in practice, I would be happy if the main user of a station could still work when the server is down).

I'm currently using NIS for this (for for passwords).  I have the main user of a station also listed in /etc/passwd and /etc/shadow (with a different password then the network).
My nsswitch.conf reads:
passwd files nis
group    files nis

This works as long as the NIS server is available, but when I unplug the logins just stall forever.

So, I'm looking at an alternative solution that still allows all users to log on to any station but still allows basic operations without the server (I ask a lot ;-) ).

Any ideas on this one?
Will ldap handle this better?
Is there a good (automated way) of synchronizing identity information? 

Thanks

---

### Post by hardcandy on 2005-01-07
Could you use rsync to do this? Set up rsync to update the clients and the server? You can limit rsync to update just one file or directory and use ssh to do it.
 From Marcel Gagne (Cooking With Linux):
[http://www.informit.com/articles/article.asp?p=100666&redir=1](http://www.informit.com/articles/article.asp?p=100666&redir=1)

---

### Post by hardcandy on 2005-01-07
And I got curious and drync is available in the warty repository. 
"Two-way remote file synchronisation
drsync.pl uses rsync to synchronise between two directories
(local or remote), but stores state information for files,
so that it can be used in both directions, and can
cope with files created, modified or deleted in either
repository."

---

