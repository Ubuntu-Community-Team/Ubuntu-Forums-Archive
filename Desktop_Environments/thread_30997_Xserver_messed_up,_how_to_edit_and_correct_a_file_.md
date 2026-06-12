---
title: "Xserver messed up, how to edit and correct a file in 'dos' mode?"
date: 2005-05-01
forum: Desktop Environments
---

### Post by Dex on 2005-05-01
I have accidentally edited and messed up xorg.conf file but luckily I had xorg.conf.bak for it. I could not get into X server because of the problem, but deleted corrupted and renamed .bak file to the original and all was ok. My questions is - what if I didn't have a .bak file - how do I edit and save the corrupted file while not in X windows, but only in 'dos' like screen? Noob here, couldn't find this on the forum anywhere else

---

### Post by Laurent Cazalet on 2005-05-01
wise you had kept a backup file.

In the mode called "console", you just need to type

```
sudo dpkg-reconfigure xserver-xorg
```

and you'll be taken through the xorg server reconfiguration. it will recreate a xorg.conf file with the value you are prompted for.

---

### Post by Fab on 2005-05-01
[QUOTE=Dex]I have accidentally edited and messed up xorg.conf file but luckily I had xorg.conf.bak for it. I could not get into X server because of the problem, but deleted corrupted and renamed .bak file to the original and all was ok. My questions is - what if I didn't have a .bak file - how do I edit and save the corrupted file while not in X windows, but only in 'dos' like screen? Noob here, couldn't find this on the forum anywhere else[/QUOTE]
 vi(m) or nano are editors for the cli

but for repairing an xorg.conf, the above would probably be easier

---

### Post by bazh on 2005-05-04
Instead of renaming the backup file, copy it instead

$cp xorg.conf-bak xorg.conf

That way you still have your original backup 

:)

---

### Post by Dex on 2005-05-04
thanks, it's amazing how the most simple things that are in front of me are not obvious. My attempts to avoid the 'duh...' are not succeeding  :)

---

