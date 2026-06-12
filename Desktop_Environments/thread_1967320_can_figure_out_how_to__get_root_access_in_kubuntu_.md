---
title: "can figure out how to  get root access in kubuntu 12.04"
date: 2012-04-28
forum: Desktop Environments
---

### Post by CosmoBeep on 2012-04-28
Im trying to  add a kdm/ themes folder in  /usr/share/apps/ but it keeps saying  access denied an i tried sudo and  sudo -i but it wont allow me to make a folder.

---

### Post by zombifier25 on 2012-04-28
Is your user an administrator (aka allowed to sudo)?

---

### Post by CosmoBeep on 2012-04-28
not sure i dont know how to check.

---

### Post by DeceptiveHornet on 2012-04-28
sudo apt-get update
sudo apt-get upgrade

If it whines about not having sudo access, then you'll know :)

---

### Post by CosmoBeep on 2012-04-28
sudo apt-get update worked. but sudo wont work for the root.

---

