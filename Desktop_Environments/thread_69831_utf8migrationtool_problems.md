---
title: "utf8migrationtool problems"
date: 2005-09-28
forum: Desktop Environments
---

### Post by Gustav on 2005-09-28
Somehow utf8migrationtool wasn't installed and run when I upgraded to Hoary from Warty so I tried to run it now.

It did a good job reconfiguring my locales but it didn't change my file-names. All I got was this:
```
$ utf8migrationtool
Traceback (most recent call last):
  File "/usr/bin/utf8migrationtool", line 91, in change_setup
    os.rename(oldfile, newfile)
OSError: [Errno 2] Filen eller katalogen finns inte
```
(the last part means "The file or catalogue does not exist")

After changing the /usr/bin/utf8migrationtool so that it would catch these errors I found out that the same error were thrown for all my files.

Anyone that can help me?

PS. I tried running it with sudo but that didn't help

---

