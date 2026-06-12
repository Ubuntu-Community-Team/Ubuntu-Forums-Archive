---
title: "Q: How to vew currently installed packages in terminal"
date: 2006-08-10
forum: Desktop Environments
---

### Post by Mandor on 2006-08-10
I searched here and google, but I didn't find a conveniet way to search/list only the currently installed packages using apt-get, apt-cache or aptitude. I would appreciate if someone shares some experienxe (a useful alias or something).

Thank you in advance :)

---

### Post by aysiu on 2006-08-10
```
dpkg -l
```

---

### Post by etank on 2006-08-10
Type ```
dpkg -l | less
```That should give you a list of all packages installed through apt-get, aptitude or Synaptec. Apps that you have compiled will probably not be shown.

---

### Post by Mandor on 2006-08-10
Big thanks, it's very stupid that I didn't checked dpkg.

---

