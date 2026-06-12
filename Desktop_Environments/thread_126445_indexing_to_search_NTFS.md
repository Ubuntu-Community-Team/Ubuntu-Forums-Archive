---
title: "indexing to search NTFS"
date: 2006-02-06
forum: Desktop Environments
---

### Post by Zelut on 2006-02-06
I've got an NTFS mounted drive in my system as part of a system restore for a client.  I need to backup & remove all .jpg, .doc, etc but I am not able to 'updatedb' to index the drive & do a search on anything.

Is there a way to do this?  Am I limited to manually searching via ls?

Thanks.

---

### Post by gkolomvos on 2008-01-05
try to open a terminal and use the following command 

find .  -name *.jpg

Consult manual to see how find works (man find)

gkolomvos

---

