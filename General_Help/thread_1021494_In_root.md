---
title: "In root"
date: 2008-12-25
forum: General Help
---

### Post by dvotruba on 2008-12-25
Many thins I try to do say I have to be in root. Why and how? Also installed a modem locator and it says it has to be in the root directory, but it won't let me copy there?

Thanks
New User
Doug

---

### Post by taurus on 2008-12-25
In Ubuntu, you use sudo/gksudo if you need root privilege.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by cariboo on 2008-12-25
To become root you use the sudo command in a terminal or gksu for graphical applications for example to edit a configuration file, press ALt-F2 and type:

```
gksu gedit /boot/grub/menu.lst
```

and for example to move some files to a directory you don't own, in a termianl type:

```
sudo mv somefile /usr/local/bin
```

If you need to be root for a number of operations that will take longer than the sudo timeout allows, in a terminal type:

```
sudo -i
```

The above command will drop you to a root prompt.

Jim

---

