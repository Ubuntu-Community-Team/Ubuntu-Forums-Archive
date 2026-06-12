---
title: "Where do deleted files go?"
date: 2006-04-30
forum: Desktop Environments
---

### Post by TheIdiotThatIsMe on 2006-04-30
I had problems with permissions deleting certain folders/files under one of my accounts even though I had correct permissions (trying to delete old music files for space). So I opened nautilus as root and deleted them. But I realized now they wont appear in my trash, so I dont know how to permanently delete them. Where do files go that were deleted as root from under nautilus?

---

### Post by rado_london on 2006-04-30
Did you search thee files in /root/.Trash ?

---

### Post by Ramses de Norre on 2006-04-30
Maybe /root/.Trash, otherwise look for folder mountpoint/.Trash-root.

---

### Post by TheIdiotThatIsMe on 2006-04-30
[QUOTE=rado_london]Did you search thee files in /root/.Trash ?[/QUOTE]

Thanks a bunch, that was it!

---

