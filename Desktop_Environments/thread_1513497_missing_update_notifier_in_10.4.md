---
title: "missing update notifier in 10.4"
date: 2010-06-19
forum: Desktop Environments
---

### Post by ssalman on 2010-06-19
So hopefully this is a quick question: I toyed with my desktop panels, and now I don't see my update notifications, although I can see every thing else. I have the notification area and indicator applt session on my panel but still can't see the update notification, when running "ps -A| grep update-notifier" I find it running.... what am I missing... I know it must be simple, but I can't find it.... any help is appreciated. Thanks.

---

### Post by ajgreeny on 2010-06-19
You need the **Indicator applet**, not **Indicator applet session** for that to show.  The two are quite different things.

---

### Post by ssalman on 2010-06-20
> **ajgreeny said:**
> You need the **Indicator applet**, not **Indicator applet session** for that to show.  The two are quite different things.

Thanks ajgreeny, actually upon further search I found that I do have both Indicator applet and Indicator applet session, but still my update notifications are no where to be found. any ideas?

---

