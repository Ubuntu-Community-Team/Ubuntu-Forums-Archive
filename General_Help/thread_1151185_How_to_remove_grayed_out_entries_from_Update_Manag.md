---
title: "How to remove grayed out entries from Update Manager?"
date: 2009-05-06
forum: General Help
---

### Post by Razmear on 2009-05-06
After my upgrade to 9.04 I was left with a grayed out gstreamer plugins bad in my update manager and today I had a partial upgrade happen and was left with two more entries grayed out and stuck in the update manager screen (linux restricted modules + generic). 

Is there a way to get these cleaned out of update manager so I only see updates that will actually install? 

Thanks,
eb

---

### Post by zvacet on 2009-05-06
I don´t know why they are not installed but try

```
sudo apt-get update && sudo apt-get upgrade
```

---

