---
title: "Broken GNOME Help Icon?"
date: 2005-11-04
forum: Desktop Environments
---

### Post by James_Nostack on 2005-11-04
Hi - I installed Breezy today.  On my top panel is a red and white "Life Preserver" icon, that says "Help - Get Help with GNOME"

But... it gives me an error message:
[i]**Cannot Launch Icon**
Details: Failed to execute child process "yelp" (No such file or directory)[/i]

Any advice?  I'm wondering if something may have happened during installation?

thx in advance,

---

### Post by Xian on 2005-11-04
Make sure you have yelp installed.

```
$ sudo apt-get install yelp
```

---

### Post by James_Nostack on 2005-11-05
Thank you Xian, that worked perfectly!

---

