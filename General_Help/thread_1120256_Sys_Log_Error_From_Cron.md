---
title: "Sys Log Error From Cron"
date: 2009-04-08
forum: General Help
---

### Post by measekite on 2009-04-08
When running Cron to backup files to a USB NTFS drive I get the following errors:


```
Apr  8 16:40:02 dcx-client-1 ntfs-3g[17168]: Not enough space to extended mft data attribute. 

Apr  8 16:40:02 dcx-client-1 ntfs-3g[17168]: Could not allocate new MFT record
```

It was running in the past.

---

### Post by dcstar on 2009-04-09
> **measekite said:**
> When running Cron to backup files to a USB NTFS drive I get the following errors:


```
Apr  8 16:40:02 dcx-client-1 ntfs-3g[17168]: Not enough space to extended mft data attribute. 

Apr  8 16:40:02 dcx-client-1 ntfs-3g[17168]: Could not allocate new MFT record
```

It was running in the past.

Do a fsck on it.

---

