---
title: "Unreal Tournament 2004 Dual Boot?"
date: 2007-12-06
forum: Gaming &amp; Leisure
---

### Post by Invalidx on 2007-12-06
I have an XP/Ubuntu Dual Boot on my laptop
and I'm wondering, is there a way to have a shared install of UT2004, my XP can read my home drive [fs-driver.org]

---

### Post by Cappy on 2007-12-07
Yes, I've done this. In my case I had all the data on my windows drive and for all of linux UT2004 directories (except "local" ones such as cache and system) I sim-linked them to the same windows folders.

A sample of doing this could look like
```
sudo mv /ut2004install/Textures /ut2004install/Textures.old
sudo ln -s "/media/windows/program files/ut2004/Textures" ut2004install/Textures

```

If instead you want to keep UT2004 on linux you'll need to either move the windows System folder in the linux install or change the ini to tell it that the UT2004 folders are located somewhere else. I've tried the second suggestion in the last sentence before and it wouldn't work for me but it might have been a fluke.

---

### Post by Invalidx on 2007-12-09
I was thinking of trying to install it in linux in /home/jamie/programs, then going on to windows, and installing it in X:/home/jamie/programs too, it would then have all the needed files in XP, and linux, but 
I'm worried it may screw up something important?

---

