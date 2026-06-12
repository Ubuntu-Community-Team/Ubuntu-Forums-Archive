---
title: "Nautilus crashes when opening folder.  Upgrade kernel to 2.6.22-10 generic"
date: 2007-08-25
forum: Desktop Environments
---

### Post by sparckis on 2007-08-25
Hi,
    I just upgraded to kernel 2.6.22 using the post [http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)

Everything went ok, but now when I open nautilus and just try to navigate, it dies whenever I double click on a folder.  It then re-launches nautilus and I am back in my home directory.  I can right click on a folder and choose open and this will work.  

Lil help?

---

### Post by reset3x on 2007-08-28
> **sparckis said:**
> Hi,
    I just upgraded to kernel 2.6.22 using the post [http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)

Everything went ok, but now when I open nautilus and just try to navigate, it dies whenever I double click on a folder.  It then re-launches nautilus and I am back in my home directory.  I can right click on a folder and choose open and this will work.  

Lil help?

```
sudo aptitude purge nautilus
```

```
sudo apt-get install nautilus
```

Good Luck!!!

Peace to You!!!

---

