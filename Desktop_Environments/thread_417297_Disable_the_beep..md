---
title: "Disable the beep."
date: 2007-04-21
forum: Desktop Environments
---

### Post by st33med on 2007-04-21
Usually, whenever I delete anything in terminal, it beeps. How do I disable the beeping?

---

### Post by Jussi Kukkonen on 2007-04-21
To prevent beeps altogether add this line into */etc/modprobe.d/blacklist*:
```
blacklist pcspkr
```

---

### Post by st33med on 2007-04-21
Thanks that helped me from annoying other people, including myself!:popcorn:

---

