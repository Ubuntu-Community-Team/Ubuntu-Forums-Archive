---
title: "Firefox Changes Do Not Stay"
date: 2009-02-10
forum: General Help
---

### Post by kshane on 2009-02-10
Hi all!

My wife has a separate login for her own desktop setup in Ubuntu.  She has Firefox 3.0.5.  She cannot save any changes she makes using the edit>preferences.  For example, she wants "my.yahoo" for her homepage, but after entering it and testing it (with clicking the "homepage" button) it works, but when she shuts down and restarts Firefox, the changes are ALL lost!

I have removed and reinstalled Firefox and there's no difference - still doesn't save changes.
 HELP!!!  It's driving me insane!!!

---

### Post by Irony on 2009-02-10
In terminal type;

```
mv ~/.mozilla ~/.mozilla1
```

Then start Firefox. Note you will lose any setting doing this but the above command has changed the file name of your current .mozilla  to .mozilla1.

---

