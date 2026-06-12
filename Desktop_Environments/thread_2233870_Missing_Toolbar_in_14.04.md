---
title: "Missing Toolbar in 14.04"
date: 2014-07-11
forum: Desktop Environments
---

### Post by Keith65rider on 2014-07-11
Hi there, Ubuntu 14.04 boots up showing only the desktop with a few files and photos that I have on it. There is no toolbat and no menue bar, so I cannot acces anything. Has anyone any ideas please?

keith65rider

---

### Post by Frogs Hair on 2014-07-11
If you can access the terminal using Ctrl+Alt+T run the following command to reset Unity . ```
 setsid unity
```

---

### Post by Keith65rider on 2014-07-12
No. I cannot access the Terminal.

 Thats the problem.

---

### Post by Frogs Hair on 2014-07-12
Please include some information about your computer hardware and whether or not you are using proprietary graphics drivers.

---

### Post by kostkon on 2014-07-12
> **Keith65rider said:**
> No. I cannot access the Terminal.

 Thats the problem.
Login and boot into your desktop, then press CTRL+ALT+F1 (to F6) to access TTY (and to go back to the desktop, press CTRL+ALT+F7. More about TTY [here]("http://askubuntu.com/questions/66195/what-is-a-tty-and-how-do-i-access-a-tty")) and then follow the instructions here on [how to reset your unity/compiz]("http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html").

Hope that helps.

---

