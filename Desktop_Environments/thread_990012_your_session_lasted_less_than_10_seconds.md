---
title: "your session lasted less than 10 seconds"
date: 2008-11-22
forum: Desktop Environments
---

### Post by mexybaby on 2008-11-22
I have this problem when I start gnome: "Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem" in the error report appears that it wasn't possible to load the shared library 
"error while loading shared libraries: libasound.so.2: cannot open shared object file: no such file or directory
What should I do? It's possible to solve the problem reinstalling gnome? Or How can I do it from the failsafe terminal
Thank you for any help :confused: :confused: :confused: :confused: :confused: :confused:

---

### Post by taurus on 2008-11-22
At the GUI login screen, press <Ctrl><Alt>F2 to get to a console.  Then, log in with your username and password.  Now, check to see if your machine is really running out of disk space.

```
df -h
```

---

### Post by mexybaby on 2008-11-22
> **taurus said:**
> At the GUI login screen, press <Ctrl><Alt>F2 to get to a console.  Then, log in with your username and password.  Now, check to see if your machine is really running out of disk space.

```
df -h
```

Thanks for ur prompt response not running out of disk space.The most used partition is just 16%.

---

