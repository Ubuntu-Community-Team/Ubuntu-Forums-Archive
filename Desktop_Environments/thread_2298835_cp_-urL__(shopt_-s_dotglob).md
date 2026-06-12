---
title: "cp -urL  (shopt -s dotglob)"
date: 2015-10-14
forum: Desktop Environments
---

### Post by joe.koenig on 2015-10-14
I was about  to do my poor-mans-Backup-routine, which, as of recently, includes:

$ cp -urL ~/000\ \ \ to\ backup/* /mnt/external_USB_HD/000\ \ \ \ \ \ \ updates\ \ \ \ \ from\ \ \ \ \ lubuntu/

 (abbreviated:  $ cp -urL source/* destination/)

Feel free to laugh at me, but the source folder contains a file named ".bashrc", which doesn't get uppdated ...
   ... now, while I'm writing this, I rememeber I'd have to set

 $ shopt -s dotglob

beforehand.

*Duh*

Yeah, don't stop laughing.  The show is still going on.

---

