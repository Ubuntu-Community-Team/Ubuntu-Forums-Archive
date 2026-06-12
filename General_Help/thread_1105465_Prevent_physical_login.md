---
title: "Prevent physical login"
date: 2009-03-24
forum: General Help
---

### Post by kamasabi on 2009-03-24
Hey ya'll,

I have a file server (ubuntu 7.10) and I have most of my file access permissions all done through smb.conf for network shared directories.  However, the users I had set up are able to log in to the server if they were actually sitting right in front of it.  I would like to disable this feature, but still allow them access to network shared files.  Is there an easy method of doing this?

---

### Post by Iowan on 2009-03-24
One option might be to change the login shell setting in /etc/passwd from /bin/sh (or bash, or whatever) to /bin/false.

---

### Post by kamasabi on 2009-03-25
perfect, that did the trick, thanks!

---

