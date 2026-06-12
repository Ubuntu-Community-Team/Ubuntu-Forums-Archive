---
title: "permissions"
date: 2007-05-15
forum: Desktop Effects &amp; Customization
---

### Post by jlkz on 2007-05-15
permissions i just installed Ubuntu and I'm trying to customize and i found out i can't save things in to the folders i need to they say the owner is root and i can't change it. also i dont know how to login to root.

---

### Post by reacocard on 2007-05-15
> **jlkz said:**
> permissions i just installed Ubuntu and I'm trying to customize and i found out i can't save things in to the folders i need to they say the owner is root and i can't change it. also i dont know how to login to root.

Just use
```
sudo <command>
```
and enter your login password when prompted. Use gksudo for GUI apps. 'sudo -s -H' will give you a full root terminal.

---

### Post by jlkz on 2007-05-15
ok it says

 root@jk:~# 

now i still don't know how to change the permissions

thanks

---

### Post by reacocard on 2007-05-15
Don't change the permissions, just edit as you need with root, then log out of the root terminal.

More info: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by jlkz on 2007-05-15
but thats a lot of work for every time i need to save a file in a folder

---

### Post by reacocard on 2007-05-15
> **jlkz said:**
> but thats a lot of work for every time i need to save a file in a folder

What folder? If its not in /media or /home, it should be owned by root. Besides, how hard it it to use 'gksudo gedit <filename>'? You really shouldn't need to edit anything outside of /home or /media in your daily use.

---

### Post by jlkz on 2007-05-15
Its all the folders in file system it says owner by root but i can't edit them.

---

### Post by reacocard on 2007-05-15
> **jlkz said:**
> Its all the folders in file system it says owner by root but i can't edit them.

That's exactly how it's supposed to be. All your personal files are supposed to go into /home/<username>, and other drives go under /media. Everything else is system files, which you shouldn't touch without knowing exactly what you're doing.

---

