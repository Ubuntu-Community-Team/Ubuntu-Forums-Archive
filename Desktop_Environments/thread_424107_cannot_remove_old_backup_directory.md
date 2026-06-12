---
title: "cannot remove old backup directory"
date: 2007-04-26
forum: Desktop Environments
---

### Post by wormeyman on 2007-04-26
I'm backing up my files for my fiesty install using [a simple command]("http://ubuntuforums.org/showthread.php?t=35087") but it got stuck on var/backup i went to investigate and it was 21 GB :O the folder /var/backup is owned by root and i think that some program i ran in the dapper days was making backups there each night how do i remove that directory from my file system?  I have added it to my exclude list but i want it gone it's taking up a lot of space.

Edit:// nevermind i right clicked and used the root nautilus here script to delete it.

---

### Post by taurus on 2007-04-26
```
sudo rm /var/backup/**filename**
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

