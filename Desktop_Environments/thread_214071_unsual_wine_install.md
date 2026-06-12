---
title: "unsual wine install"
date: 2006-07-12
forum: Desktop Environments
---

### Post by mcman42 on 2006-07-12
Greets all! I have to hdd's one is mounted as / and the other is /media/hdd2 . I am getting short of free space on / so I want to install wine to /media/hdd2/.wine  can anyone guide me through this?

---

### Post by mcman42 on 2006-07-12
Just got an idea. Is it possible to move .wine dirrectory to the other hdd and just to create a link to it?

---

### Post by Bagnaj97 on 2006-07-12
> **mcman42 said:**
> Greets all! I have to hdd's one is mounted as / and the other is /media/hdd2 . I am getting short of free space on / so I want to install wine to /media/hdd2/.wine  can anyone guide me through this?

Move the .wine directory to /media/hdd2/.wine using ```
mv ~/.wine /media/hdd2/
```

then create a symlink to its old location using ```
ln -s /media/hdd2/.wine ~/.wine
```

---

