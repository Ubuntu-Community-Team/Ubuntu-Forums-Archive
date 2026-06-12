---
title: "cannot save sftp symbolic links"
date: 2009-01-15
forum: Desktop Environments
---

### Post by xiphosurus on 2009-01-15
i have some files which are symbolic links to a remote system. the links are symbolic links to "sftp://user@server:1234/home/user/file"

i used to be able to write to them transparently as if they were local files. but now that doesn't seem to work anymore.

for example, one is an excel file. they open fine with openoffice, but when i try to save changes it reports "Error saving the documents to file.xls: General input/output error while accessing /home/Desktop/user/file.xls."

in another example, one of those links is to a zip file. opens fine with fileroller, but when saving, it overwrites the symbolic link, and the symbolic link becomes a regular file! changes are not propagated to the remote file.

this only occurs as a symbolic link. when making changes by opening the remote files directly through sftp on nautilus, both fileroller and openoffice work perfectly.

is anybody experiencing this? thanks in advance.

---

