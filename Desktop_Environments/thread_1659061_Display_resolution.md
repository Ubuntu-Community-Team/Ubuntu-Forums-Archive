---
title: "Display resolution"
date: 2011-01-03
forum: Desktop Environments
---

### Post by ventsyv on 2011-01-03
After installing Ubuntu 10.10 there are only 2 or 3 resolution options for the display, the highest of which is 800x600. I have a 19" Dell monitor so obviously the resolution will be much higher.

I suspect I have to mess with the xOrg config file. I have very bad memories doing that a bunch of years ago, so I would prefer if I can use some kind of GUI. Is ARardR the way to go? Why doesn't the default utility support resolutions higher than 800x600 ?

Thanks.

---

### Post by wojox on 2011-01-03
What Graphics Card/Chip do you run?

```
lspci | grep VGA
```

---

### Post by ventsyv on 2011-01-03
I'm not in front of the machine right now. It's either an old Radeon or an integrated intel chip. It's probably 5 years old.

---

### Post by wojox on 2011-01-03
Try [Xrandr]("https://wiki.ubuntu.com/X/Config/Resolution")

---

