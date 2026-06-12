---
title: "Removable Media - Import Camera"
date: 2006-10-28
forum: Desktop Environments
---

### Post by Mau on 2006-10-28
So, I'm trying to configure my system to automatically launch F-Spot and start the import process.  I figured out that I need to change Removable Drives and Media Preferences -> Cameras -> Digital Camera to "f-spot --import %h".  This will launch F-Spot and open the import window, but won't automatically select the camera.  I suspect %h is wrong.  What is the replacement variable?

---

### Post by Mau on 2006-10-29
Actually, can someone just tell me the default value for Removable Drives and Media Preferences -> Cameras -> Digital Camera?

---

### Post by Mau on 2006-10-29
Anyone have it?

---

### Post by chenel on 2006-10-30
```
gnome-volume-manager-gthumb %h
```

However, I do think %h is right, because I have a similar problem with gthumb... it starts fine if I type the command in to a terminal, but when I plug the camera in, I don't get the auto-start that I used to in Dapper.  So it seems there is a different problem...

---

### Post by easy_target on 2006-11-28
Same problem here. Any kind soul?

---

### Post by easy_target on 2006-11-29
Did anyone get this going? Is it broken in edgy?

---

### Post by chenel on 2006-12-02
Have a look at [this thread]("http://ubuntuforums.org/showthread.php?p=1834654") -- it fixed things for me.

-chenel

---

