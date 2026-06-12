---
title: "little help with Incremental tar"
date: 2009-04-30
forum: General Help
---

### Post by saeeddeep on 2009-04-30
a little more help with tar !!
Using a full & incremental backup script, I have a full backup archive each Thursday, named "Thu-23Apr.tar" for example. and incremental backup from Sunday, "Sun-26Apr.tar" to Wednesday, "Wed-29Apr.tar"... Nice.
I want to extract a certain directory"/data/public/documents/" including all subdirectories and files; as far as I know:
$ tar --extract --file Thu-23Apr.tar /data/public/documents
::: Then :::
$ tar --extract --listed-incremental --file Wed-29Apr.tar /data/public/documents
Need a confirm ??

##Sorry, if  it's a duplicated thread !!

---

