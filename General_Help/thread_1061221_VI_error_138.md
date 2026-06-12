---
title: "VI error 138"
date: 2009-02-05
forum: General Help
---

### Post by Lilit on 2009-02-05
All of a sudden my VIM started outputting the Error 138 -
E138: Can't write viminfo file [NULL]!
when trying to close the file using :q or :q! commands.

The system runs fine, after browsing for similar posts I tried the following:

1. Rebooted the system.
2. Manually deleted "viminfo" file
3. added "env_reset" into Defaults section of /etc/sudoers

Any suggestions please.

Thanks in advance,
Lilit

---

### Post by Lilit on 2009-02-05
Found the source:

Previously not all the "viminfo"-s were deleted.

---

