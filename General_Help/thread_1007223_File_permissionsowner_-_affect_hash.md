---
title: "File permissions/owner - affect hash?"
date: 2008-12-10
forum: General Help
---

### Post by ImpelGD on 2008-12-10
Hello all,

I was wondering if files having different permissions/owners would make a difference to the hash of a file. I'm planning to check our extensive music collection with md5deep (would like to dump to text file rather than command line if anyone knows how), but before I install and get my brother to install, etc. I thought I should check about this query.

Many thanks.

---

### Post by Titan8990 on 2008-12-10
No, file permissions are not kept in a single file. The only hashes in /etc/shaddow are your passwords.


As far as getting md5deep to output to a text file, that should be pretty basic but I have not tried it. 


To direct standard output to a file:


COMMAND > FILE.TXT


Just use a > and then specify the name of the file you want to give its output to.

---

