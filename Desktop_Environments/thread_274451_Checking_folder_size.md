---
title: "Checking folder size"
date: 2006-10-09
forum: Desktop Environments
---

### Post by textguru on 2006-10-09
How can I check folder size? :confused:

---

### Post by kidders on 2006-10-09
Hi there,

You could try **du -hs folderpath**

---

### Post by bswilson on 2006-10-09
Just go to the folder you're interested in in the Terminal, and run this command:

```
$ du -chks
```

This will summarize the recursive disk utilization for the folder you're in at the time.

---

### Post by textguru on 2006-10-09
thanks for the reply. I appreciate it.

---

### Post by varean on 2006-10-09
Also, you can right click on the folder and click on "properties."

---

### Post by textguru on 2006-10-11
> **varean said:**
> Also, you can right click on the folder and click on "properties."

Thanks for the reply. I didn't tell you that I am using server edition of ubuntu.:mrgreen:

---

