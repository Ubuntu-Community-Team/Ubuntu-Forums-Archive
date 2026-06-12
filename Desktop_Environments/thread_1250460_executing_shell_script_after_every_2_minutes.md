---
title: "executing shell script after every 2 minutes"
date: 2009-08-26
forum: Desktop Environments
---

### Post by Vinod_hire on 2009-08-26
how to eceute shell script after every 2 minutes

---

### Post by slakkie on 2009-08-26
man cron
man crontab

Short version:

crontab -e and put the following sniplet in there, save and quit

```

# Run every two mins
*/2 * * * * /path/to/script
# Run 2 after the hour
2 * * * * /path/to/script

```

---

### Post by DaithiF on 2009-08-26
use crontab

```
man crontab

``` to learn more

---

