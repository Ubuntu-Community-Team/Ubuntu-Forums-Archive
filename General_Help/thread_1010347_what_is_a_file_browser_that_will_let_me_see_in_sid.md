---
title: "what is a file browser that will let me see in side my root/.config directory"
date: 2008-12-13
forum: General Help
---

### Post by jarrah-95 on 2008-12-13
i need this to fix another problem [http://ubuntuforums.org/showthread.php?p=6360286#post6360286](http://ubuntuforums.org/showthread.php?p=6360286#post6360286) and i need to be able to make a file in /xserver-xgl/ called disable

---

### Post by taurus on 2008-12-13
You mean running nautilus with root privilege?

Applications -> Accessories -> Terminal
```
gksudo nautilus
```

---

### Post by drs305 on 2008-12-13
To simply make a file, run this command (if the folder /xserver-xgl already exists):
```
sudo touch /xserver-xgl/disable 
```

or you can open nautilus with admin privileges, navigate to the folder and right click to create a new file:
```
gksudo nautilus /xserver-xgl/
```

In either case, the file will be owned by root unless you change it.

---

