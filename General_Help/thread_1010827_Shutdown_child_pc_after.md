---
title: "Shutdown child pc after"
date: 2008-12-14
forum: General Help
---

### Post by Waappu on 2008-12-14
Hi

I need script that shutdown pc e.g. between 7pm - 7am when specific user login. Idea is prevent children using pc on that time.

I have seen some post in this forum in some point but can not find it anymore.

Also if you can point me to some net filter that blocks adult content.

Thanks advance

---

### Post by jonabyte on 2008-12-14
```

#!/bin/bash
shutdown -h now


```

place the code in cron and edit.

Not sure how you would prevent someone from turning it back on.

---

### Post by Waappu on 2008-12-14
So if I can have script when user login it checks if clock is between 7pm - 7am and if it is then it runs
```
shutdown -h now
```

---

### Post by hikaricore on 2008-12-14
You could also if you wanna be really mean set a bios password. :p

---

### Post by mike555 on 2008-12-14
[http://ubuntuforums.org/showthread.php?t=887769](http://ubuntuforums.org/showthread.php?t=887769)

---

