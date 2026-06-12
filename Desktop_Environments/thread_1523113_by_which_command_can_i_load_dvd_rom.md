---
title: "by which command can i load dvd rom"
date: 2010-07-03
forum: Desktop Environments
---

### Post by justwarm on 2010-07-03
as the command "eject" i can eject dvd like that way i need a command to lod dvd .

---

### Post by sisco311 on 2010-07-07
```
eject -t
```

Or to close it if it's opened and open it if it's closed:
```
eject -T
```

Read the man page for more options:
```
man eject
```

---

