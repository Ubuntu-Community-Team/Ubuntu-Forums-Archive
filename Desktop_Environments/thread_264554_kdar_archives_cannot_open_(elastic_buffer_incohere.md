---
title: "kdar archives: cannot open (elastic buffer incoherent structure)"
date: 2006-09-24
forum: Desktop Environments
---

### Post by daryl314 on 2006-09-24
hi all,

kdar doesn't appear to be working, although it has in the past.  i am able to open old archives without a problem, but whenever i try to open newly created archives, i get the error:

```
Extracting contents of the archive...
too large elastic buffer or elastic buffer incoherent structure
Error: unable to open the archive.
```

this happens with a small archive file (~300 Mb) as well as archive files i have made directly with dar.  does anyone have any thoughts about why this could be happening?

thanks,
daryl

---

### Post by daryl314 on 2006-09-27
it seems that the error only occurs when i open an unencrypted archive file.

---

### Post by daryl314 on 2006-09-27
i found the answer on the sourceforge forum.  in case anyone else has this problem, the answer is that you have to make sure that the default is not using encryption in the crypto settings.

---

