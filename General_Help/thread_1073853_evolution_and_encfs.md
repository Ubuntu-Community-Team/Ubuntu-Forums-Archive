---
title: "evolution and encfs?"
date: 2009-02-18
forum: General Help
---

### Post by andman on 2009-02-18
Hi, I've done some extensive searching but can't find any solution for this one. 

I've set up an encfs filesystem.
/home/andman/.encfs with mount point /home/andman/encfs

I'd like to encrypt my email. Evolutions default directory is under home/andman/.evolution. I tar'd .evolution and un-tarred it under /home/andman/encfs/.evolution.

I then created a symbolic link:
lrwxrwxrwx 1 andman andman 30 2009-02-18 15:14 .evolution -> /home/andman/encfs/.evolution

When trying to retrieve a message from the inbox, evolution returns the following error. 

Timed out trying to get lock file on /home/andman/.evolution/mail/local/Inbox. Try again later.

I went back and created a symbolic link under another un-encrypted directory and all works, so seems to be an encfs/Evolution thing...

Any ideas?

---

