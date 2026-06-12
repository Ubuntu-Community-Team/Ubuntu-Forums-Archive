---
title: "Run multiple instance of xautolock?"
date: 2008-08-16
forum: Desktop Environments
---

### Post by carleton on 2008-08-16
Hey everyone is there a simple way to set multiple commands in xautolock? I want to set a command to activate in both the top left and bottom left corners. 

the first command is 

```
xautolock -locker  "xte 'key Scroll_Lock'" -corners +000  -cornerdelay 0 &
```


The second is 

```

xautolock -locker  "xte 'key F12'" -corners 00+0  -cornerdelay 1 &
```

I can run one, but when I try to run the second  I get
```

xautolock is already running (PID 20393).
```

I'm sure this a really simple fix, but I'm a bit of a noob. I couldn't find much about this, any help would be appreciated.

Cheers

---

