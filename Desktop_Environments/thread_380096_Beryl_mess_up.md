---
title: "Beryl mess up"
date: 2007-03-09
forum: Desktop Environments
---

### Post by hammadr89 on 2007-03-09
Guess I should have heeded that warning. Just installed it, then when I tried to run it, the system froze. So I restarted, and turns out there's something wrong with the X server, so I can't start Ubuntu. Anyway I can repair it using the recovery console?

---

### Post by PriceChild on 2007-03-09
```
sudo dpkg-reconfigure xserver-xorg -phigh
```Will reconfigure your x server to defaults.

---

### Post by hammadr89 on 2007-03-09
Worked great, thanks :)

---

### Post by PriceChild on 2007-03-09
Good to hear :)

*marks resolved*

---

