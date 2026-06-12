---
title: "Unison should ignore permissions stamp"
date: 2009-06-15
forum: General Help
---

### Post by StevoSn on 2009-06-15
hi!

I am using unison to sync some data between my external HDD and Desktop. I use a configuration file for the path and so on..

whenever I start it unison detects changes in every file and tries to sync every file. This is because I sync between a NTFS and a Ext3 filesystem. Since on the NTFS there is no permissions stamp like every file has on ext3.

is there a way of ignoring the permissions?

thanks for any help!

---

### Post by StevoSn on 2009-06-15
okay.. I guess I solved it:

there's an option "perms" that I use now like this within a configuration file

perms = 0

just in case someone needs it someday..

cheers!

---

### Post by Slate8 on 2010-04-09
Thanks this really helped me. I was syncing from ext3 to ntfs and this totally sorted the permissions issue that was causing Unison to fail.

Thanks again.

---

