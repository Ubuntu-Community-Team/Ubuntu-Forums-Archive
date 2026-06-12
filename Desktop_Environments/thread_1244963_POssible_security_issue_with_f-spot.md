---
title: "POssible security issue with f-spot"
date: 2009-08-20
forum: Desktop Environments
---

### Post by mcglnx on 2009-08-20
Dear All,

I found a security issue with f-spot. It does not (at first sight) put desktop at risk.

I'm trying to use f-spot for the family. For this I create a shared location for f-spot directory and metadata repository. I ```
chgrp family -Rf * 
``` the directory and do a ```
chmod -R g+s; chmod -R g+w *
```. All my users have a umask=002

If I create a file with any file using the terminal with any user, I got the correct group and rights inherited. However, f-spot is breaking this and do a chmod g-rw of each newly created file. Other user will get a lot of nasty Win32 (sigh!) errors while f-spot will read these files.

Is it a bug? Is there any workaround? Should I consider alternative to f-spot?

Cheers,
M.

---

