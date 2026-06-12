---
title: "xmodmap failing to be loaded"
date: 2006-08-04
forum: Desktop Environments
---

### Post by frying_fish on 2006-08-04
I created an xmodmap to deal with keys on my remote control and up until recently it worked flawlessly, being loaded every time X has started, however in the last 3 days it has stopped loading the xmodmap.

performing:
```

cat /var/log/Xorg.0.log | grep xmodmap

```

returns nothing, suggesting to me that its not even checking it anymore.  The appropriate line is still in /etc/gdm/gdm.conf-custom

So I am a bit at a loss, if anyone knows how to sort this out, it will be appreciated

---

