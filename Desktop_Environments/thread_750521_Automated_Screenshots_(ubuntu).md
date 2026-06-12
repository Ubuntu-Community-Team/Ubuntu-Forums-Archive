---
title: "Automated Screenshots (ubuntu)"
date: 2008-04-10
forum: Desktop Environments
---

### Post by warp99 on 2008-04-10
You can run this:

```
import -window root filename.png
```

Then run this in a script as a crontab every hour. You can also do the following:

```
import -window root filename-$(date +%T-%F).png
```

That will also include the time and date if you don't want to overwrite the file.

Edit:

You need to install the imagemagick package for this to work.

---

### Post by kpkeerthi on 2008-04-10
Also, you can also use GIMP. From File menu, choose Acquire and specify the intervals.

---

