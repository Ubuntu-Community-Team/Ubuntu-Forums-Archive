---
title: "Suddenly unable to mount ntfs partition, which has all my data"
date: 2010-08-30
forum: Desktop Environments
---

### Post by johnfrith on 2010-08-30
After re-installing cups to deal with a printer problem, now I'm suddenly getting the message "Unable to mount Windows NTFS", which has all my data on it.

Anyone know what caused this, and how I can recover?

---

### Post by Dies on 2010-08-30
It's possible it was marked dirty, in which case you would need to boot into Windows and run chkdsk on it before Linux will mount it.

But it's hard to say with such a generic error message, to get a more detailed message, attempt to mount the partition manually and post the complete error message.

If you're not sure how to do that, post the output from 

```
fdisk -ls
```

so someone can help you.

---

### Post by johnfrith on 2010-08-30
Thanks for posting Dies.

I think it must have been so. I booted from a live cd, and that seems to have cleared it, 'cos I can now access as normal. Thought I was in for hard session for a while, there.

Thanks again.

---

