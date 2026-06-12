---
title: "Firefox becomes slugish"
date: 2009-06-23
forum: General Help
---

### Post by WildeBeest on 2009-06-23
OS - Jaunty
 
When I first start firefox. it's very snappy and works like expected.
As time goes on, it becomes progessively slower and slower.
 
Tab switching takes 20 seconds or more. Embedded links on pages take more than 10 seconds to become active. This behavior continues to get worse.
 
After about 3 days it becomes totally unuseable. I kill the firefox processes, restart it and all is well again.
 
I typically have 2 instances of firefox open with 10 - 15 tabs each.
 
I've tried disabling all the add-ons to no avail.
 
Any ideas?

---

### Post by lovinglinux on 2009-06-23
You could free the cache with this command:

```
sudo echo "starting" && sudo echo 3 | sudo tee /proc/sys/vm/drop_caches
```

This ain't work if the problem is memory leak. Yesterday for example, my Firefox was using 650 Mb and I don't know why. It went back to normal after restarting it.

I think you will like my new tutorial [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by WildeBeest on 2009-06-23
Thanks, I'll try that when I get home from work.

---

