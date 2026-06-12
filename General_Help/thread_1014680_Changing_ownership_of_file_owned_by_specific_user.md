---
title: "Changing ownership of file owned by specific user"
date: 2008-12-18
forum: General Help
---

### Post by ultralame on 2008-12-18
How can I run the chown/chgrp command and affect only files owned by a specific user/group?

I have a shared directory structure, and I want to change the owner for the files owned by user A to user B.  But there are lots of other files and folders owned by other users in there.

I looked at the man pages for chown and it only appears to specify by file location.

Thanks!

---

### Post by jerome1232 on 2008-12-18
It looks like the --from option does what you want. It's like the 5th option shown in the man page for chown.

```
--from=CURRENT_OWNER:CURRENT_GROUP
              change  the  owner and/or group of each file only if its current
              owner and/or group match those specified here.   Either  may  be
              omitted,  in  which case a match is not required for the omitted
              attribute.

```


edit: It seems chgrp doesn't have this option but you can use chown to change groups anyways.

---

