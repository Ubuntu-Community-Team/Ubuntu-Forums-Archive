---
title: "xubuntu bootslash appears during shutdown and bootup although i use ubuntu"
date: 2006-08-05
forum: Desktop Environments
---

### Post by baldy1324 on 2006-08-05
i have installed ubuntu from a lxf (linux format) dvd and it install xubuntu, kubuntu,and ubuntu apps all on one desktop. i have deleted (x/k)ubuntu-desktop and all the xfce and kde apps with apt. but now i get xubuntu's usplash when shutdown and bootup? i would like to know how to change it to plain old ubuntu.
thank you

---

### Post by Jagot on 2006-08-06
Try this from the terminal:

```
sudo aptitude remove xubuntu-artwork-usplash
```

---

