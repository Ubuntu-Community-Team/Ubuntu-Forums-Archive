---
title: "Set dpms at Startup"
date: 2018-01-24
forum: Desktop Environments
---

### Post by Danny_Saba on 2018-01-24
I am trying to set an ubuntu 16.04 machine to turn off the display after 5 minutes. When setting the command manually it works until the next reboot of course. 

```
xset dpms 300
```

I tried adding this to xinitrc but that didn't work. What's the best way to set &#8203;xset dpms 300 at startup?

```
(sleep 15s && xset dpms 30 60 300) &
exec compiz
```

---

