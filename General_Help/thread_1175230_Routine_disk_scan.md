---
title: "Routine disk scan"
date: 2009-05-31
forum: General Help
---

### Post by lotech on 2009-05-31
Hi there,

How do I initiate the disk scan which auto run after a number of reboots ?

---

### Post by VMC on 2009-05-31
Create a file called forcefsck:
```
sudo touch /forcefsck
```
Now reboot the system:
reboot

or

```
sudo shutdown -rF now
```

---

