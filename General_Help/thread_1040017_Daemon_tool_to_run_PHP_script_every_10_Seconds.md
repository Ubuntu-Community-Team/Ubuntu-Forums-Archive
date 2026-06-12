---
title: "Daemon tool to run PHP script every 10 Seconds"
date: 2009-01-15
forum: General Help
---

### Post by hafez on 2009-01-15
Hi all, 

I need a tool to run PHP script every 10 seconds, any ideas?

Regards,
hafez

---

### Post by hyper_ch on 2009-01-15
how about every minute?

---

### Post by KeyserSoze93 on 2009-01-15
> **hafez said:**
> Hi all, 

I need a tool to run PHP script every 10 seconds, any ideas?

Regards,
hafez

Put this in a file (called, say, runphp.sh):
```
#!/bin/bash
while [ 1 ]; do
sleep 10
php5 ~/script.php
done

```

Then run:
```
nohup bash runphp.sh& echo $! >phpid.txt
```

That will just run in the background (even if you close the terminal window), and when you want to close it, just run:

```
kill $(<~/phpid.txt)
```

---

### Post by sanketg86 on 2011-02-25
Thanks for sharing,
really helpful for me :)

Sanket Gandhi
[www.sanketgandhi.com](www.sanketgandhi.com)

---

