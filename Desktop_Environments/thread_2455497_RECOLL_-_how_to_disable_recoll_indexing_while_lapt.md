---
title: "RECOLL - how to disable recoll indexing while laptop is using battery"
date: 2020-12-21
forum: Desktop Environments
---

### Post by nicolasdiogo on 2020-12-21
Hello Community,


I am looking for a way to turn off RECOLL indexing while the laptop is running on batteries.

Ideally, RECOLL should resume indexing after 5 mins after we plug it back into mains AC.

Your suggestions would be mostly welcome.


Thanks,

---

### Post by TheFu on 2020-12-21
I don't know how to do that, except to control when indexing launches for the recoll DB.

Here's how I run it from my crontab:
```
10 4 * * * export RECOLL_CONFDIR=/d/D2/recoll-index/recoll ; nice /usr/bin/recollindex
```

That is the entry in my userid's crontab, not any system crontab. This is so the DB files are owned by my userid, not root.

If I used that on a laptop, I might change the 4:10am start time to be @DAILY instead and wrap the entire line with a script that checks to see if the laptop is on battery or not.  **acpi** can do that. I don't have access to my laptop now - it is sleeping in another part of the house, but here's part of a script that I use ever 15 minutes to let me know when it is below a certain charge:
```
#!/bin/bash

# Battery 0: Not charging, 100
BATT=$(acpi -i |grep -v capacity \
|sed -e 's/^.*[cC]harging, //g' -e 's/\%.*$//' \
|sed -e 's/^.*Discharging, //g' -e 's/\%.*$//')
```

Perhaps that will give you an idea for modifying it to your needs. Basically, if it is "Discharging", then it would be on battery so you wouldn't want to run it.

---

