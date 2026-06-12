---
title: "Problem with openoffice 3 updating..."
date: 2008-12-14
forum: General Help
---

### Post by Izek on 2008-12-14
I tried to use this command (even with sudo at the beginning)
```
echo 'deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main' >> /etc/apt/sources.list.d/openoffice.sources.list && sudo apt-get update
```

But all terminal returns is
```
bash: /etc/apt/sources.list.d/openoffice.sources.list: Permission denied
```

What should I do? Should I chmod it?

---

### Post by Izek on 2008-12-14
chmodding results in the file not found.

---

### Post by Izek on 2008-12-14
creating the file, then chmodding then trying to run the command again results in the same error.

adding it manually doesn't allow openoffice to update.

---

### Post by fooman on 2008-12-14
have you tried just adding the repo(s) manually? 

open nautilus with root privileges:

```
gksudo gedit /etc/apt/sources.list
```

copy/paste these lines to the bottom of file:

```
##repo for open office3
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main
```

save and close the file,  then update the repos and your packages:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Izek on 2008-12-14
According to the launchpad site in the other thread:

[http://ubuntuforums.org/showthread.php?t=988794](http://ubuntuforums.org/showthread.php?t=988794)

The amd64 build for hardy is still building, I can't upgrade yet.

---

