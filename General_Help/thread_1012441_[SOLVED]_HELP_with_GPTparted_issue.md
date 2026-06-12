---
title: "[SOLVED] HELP with GPT/parted issue"
date: 2008-12-15
forum: General Help
---

### Post by djbon2112 on 2008-12-15
On my fileserver I have a 2.71 TB RAID array and a 2.1 TB XFS partition. However, when I try to grow that partition using parted, I get the following:

```
Warning: Not all of the space available to /dev/sda appears to be uses, you can fix the GPT to use all of the space or continue with the current setting? Fix/Ignore?
```

I'm afraid to continue with the fix however out of fear of losing my ~1.5 TB of data, and I can't find anything about this procedure via Google. If someone can confirm that doing this won't nuke my data I'll go ahead, but I want to be sure!

EDIT: Got my confirmation [http://74.125.95.132/search?q=cache:ZCL-xaWo6u8J:wiki.linuxmce.org/index.php/GPT+%22fix+the+GPT%22&hl=en&ct=clnk&cd=1&gl=ca](http://74.125.95.132/search?q=cache:ZCL-xaWo6u8J:wiki.linuxmce.org/index.php/GPT+%22fix+the+GPT%22&hl=en&ct=clnk&cd=1&gl=ca) And it worked fine. Marked as solved.

---

