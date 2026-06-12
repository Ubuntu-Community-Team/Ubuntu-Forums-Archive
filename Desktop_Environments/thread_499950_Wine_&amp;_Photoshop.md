---
title: "Wine &amp; Photoshop"
date: 2007-07-13
forum: Desktop Environments
---

### Post by Magiczero on 2007-07-13
Hi

I have photoshop install on ubuntu but i can't get the photoshop.exe file to load.  the file is located in the /home/tanner/.wine/drive_c/Program Files/Adobe/Photoshop 7.0 driectory.  What is the command to start photoshop?

Thanks

---

### Post by bonzodog on 2007-07-13
it should be

```
wine /home/tanner/.wine/drive_c/Program Files/Adobe/Photoshop 7.0/photoshop.exe
```

from a terminal.

or cd into the dir containing the executable, and just run

```
$wine photoshop.exe
```

---

