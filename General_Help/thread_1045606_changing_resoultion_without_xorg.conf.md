---
title: "changing resoultion without xorg.conf?"
date: 2009-01-20
forum: General Help
---

### Post by asheq on 2009-01-20
I had to re-install Ubuntu. And I actually fixed the resolution problem the first time with some other command, but since I had to re-install ubuntu; it's gone again.
And I cannot find the same webpage with it.
I've googled it, and I'm not confident enough to trust myself with the xorg file.

Does anyone know the right command?
It's just a one line thing.

---

### Post by dcstar on 2009-01-20
> **asheq said:**
> I had to re-install Ubuntu. And I actually fixed the resolution problem the first time with some other command, but since I had to re-install ubuntu; it's gone again.
And I cannot find the same webpage with it.
I've googled it, and I'm not confident enough to trust myself with the xorg file.

Does anyone know the right command?
It's just a one line thing.

System-Preferences-Screen Resolution

---

### Post by asheq on 2009-01-20
My fault, I forgot to mention it's the resolution problem where the only resoulution that appears is 800x600.

---

### Post by dcstar on 2009-01-20
> **asheq said:**
> My fault, I forgot to mention it's the resolution problem where the only resoulution that appears is 800x600.

Then make sure any hardware driver is installed.

---

### Post by blackened on 2009-01-20
What sort of video card are you using?

---

### Post by asheq on 2009-01-20
The driver is installed, and i'm using nvidia

---

### Post by blackened on 2009-01-21
Did you try installing and using envyng?

```
sudo apt-get install envyng-gtk
```

That or using one of the nvidia-glx drivers available in the repos?

---

### Post by asheq on 2009-01-21
Fixed. Thanks so much. I had to restart 4 or 5 times, but it finally worked.

---

### Post by blackened on 2009-01-21
No sweat. Glad you got it going.

---

