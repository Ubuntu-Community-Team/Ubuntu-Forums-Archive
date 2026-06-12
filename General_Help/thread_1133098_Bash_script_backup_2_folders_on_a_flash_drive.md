---
title: "Bash script backup 2 folders on a flash drive"
date: 2009-04-22
forum: General Help
---

### Post by machine_VS_johnHenry on 2009-04-22
Working on a bash script.....

I have 2 folders on my desktop:
Art
Pics

I want the folders zipped up
After they're zipped, I want the files named the DATE, and put on a usb flash drive.

Seems easy enough,

Here is what I have that doesn't work:

cd Desktop
tar cvzf /media/disk/Art_"`date +%N`".tar.gz Art
tar cvzf /media/disk/Pics_"`date +%N`".tar.gz Pics

Can you help? Thx in advance

---

### Post by StuartN on 2009-04-22
Try adding a trailing slash to the paths:

tar cvzf /media/disk/Art_"`date +%N`".tar.gz Art/
tar cvzf /media/disk/Pics_"`date +%N`".tar.gz Pics/

---

### Post by machine_VS_johnHenry on 2009-04-22
**YESS!!!:guitar:WORKED.  THANKS!**

---

### Post by KyleBrandt on 2009-04-23
Little cleaner and easier to update:

```
date=$(date +%N)
tar cvzf /media/disk/Art_${date}.tar.gz Art/
tar cvzf /media/disk/Pics_${date}.tar.gz Pics/
```

---

