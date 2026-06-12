---
title: "Taking Ownership Of my files"
date: 2008-07-30
forum: Desktop Environments
---

### Post by andrew5859 on 2008-07-30
How do I go about taking ownership of the file system on Ubuntu 8.04 LTS, it's easy in Windows.  I want to be able to get into any and all of my files and folders and change permissions.  Can anyone help....Please   :)

---

### Post by tamoneya on 2008-07-30
it should be already set by default that you own everything in /home/insert_username.  However if you broke that somehow just do this.
```
sudo chown -R insert_username:insert_username /home/insert_username
```

---

### Post by Potatoj316 on 2008-07-30
its kind of dangerous to take controll of the WHOLE filesystem.  Its easy in windows because windows is not the most secure OS ever...

If you ever need to modify something outside your home directory use sudo in a terminal or nautilus as root like this
```
gksudo nautilus
```

be careful using nautilus as root as you can do some major damage to your system.  damage that may result in the need to reinstall.  You should never really need to modify those other files.

---

### Post by Ataris on 2008-07-30
When I switched to Linux, I felt that way too. Really, though, there are few reasons you need to access Root, and they're still YOUR files. Using gksudo will let you do this, but I don't see the need unless you are installing a plugin or something like that.

---

