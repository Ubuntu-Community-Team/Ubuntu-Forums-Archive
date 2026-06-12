---
title: "quick simple ? about using tar to backup root folder"
date: 2009-04-16
forum: General Help
---

### Post by k420 on 2009-04-16
Is this basiclaly the same thing > tar -cvzf /backup.tgz --one-file-system --exclude=/lost+found --exclude=/backup.tgz /
> tar -cvzf /backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys --exclude=/home --exclude=/media --exclude=/boot

Media has 3 hdd in it that are mounted
home is on another partition
I excluded the other ones becuase the tutorial here had them and it just made sense [https://help.ubuntu.com/community/BackupYourSystem/TAR]("https://help.ubuntu.com/community/BackupYourSystem/TAR")

---

