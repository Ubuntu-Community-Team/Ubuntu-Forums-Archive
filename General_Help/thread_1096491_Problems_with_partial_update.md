---
title: "Problems with partial update"
date: 2009-03-15
forum: General Help
---

### Post by budaslap on 2009-03-15
I was updating my computer, and power went out, and now when I use update manager it says I need to do a partial update etc... Which is all good and fine, except when the partial update window comes up, it says it's loading the updates, then just closes itself. I have tried restarting and retrying it, and nothing seems to work. 

The obvious fix for this would be to delete the partially downloaded files, but I don't know where Ubuntu stores these files, or if this is a known problem with a known solution, that would be helpful as well.

Thanks for your time.

---

### Post by dcstar on 2009-03-15
> **budaslap said:**
> I was updating my computer, and power went out, and now when I use update manager it says I need to do a partial update etc... Which is all good and fine, except when the partial update window comes up, it says it's loading the updates, then just closes itself. I have tried restarting and retrying it, and nothing seems to work. 

The obvious fix for this would be to delete the partially downloaded files, but I don't know where Ubuntu stores these files, or if this is a known problem with a known solution, that would be helpful as well.

Thanks for your time.

/var/cache/apt/archives

```
gksudo nautilus
``` will allow you to browse and delete any partially downloaded files (but be careful).

---

### Post by budaslap on 2009-03-15
Thank you very much dcstar, I'll give that a try.

---

