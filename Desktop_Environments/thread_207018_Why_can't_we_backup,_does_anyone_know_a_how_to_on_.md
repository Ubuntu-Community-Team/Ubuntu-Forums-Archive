---
title: "Why can't we backup, does anyone know a how to on this"
date: 2006-07-01
forum: Desktop Environments
---

### Post by Drifter on 2006-07-01
I have tried every suggustion that I can find in these  posts but I can't get a backup of anything.  For instance, using any program that has a backup feature in it will not work for me, kmymoney is one such program.

---

### Post by KenSentMe on 2006-07-01
Do you know where the backup will be stored? Maybe the program wants to store it in a folder where you don't have rights to save files.

---

### Post by deathbyswiftwind on 2006-07-01
I dont remember but there are a few programs I saw in the forums that have great backup support. Try searching for a back up program that will just backup everything

---

### Post by ardchoille on 2006-07-01
[QUOTE=Drifter]I have tried every suggustion that I can find in these  posts but I can't get a backup of anything.  For instance, using any program that has a backup feature in it will not work for me, kmymoney is one such program.[/QUOTE]
What are you wanting to back up? If you're wanting to back up the files in your $HOME directory, you can simply do:
```

cd /home && tar cjf /some/other/dir/backups.tar.bz2 username

```
where username is your user name and /some/other/dir would be something like /home/backups but you need to create this dir before backing up. I use this type of backup scheme in a daily cronjob.

---

### Post by ajgreeny on 2006-07-04
By default, kmymoney which you complained about, backs up to flopp mounted at /mnt/floppy which:-

1   doesn't exist unless you've made it.

2  does not have user permission anyway.

You need to make a mount point for a floppy (or other backup media) somewhere in your home folder, and then mount the floppy before you backup.  If you try to backup to the ubuntu default mount point for floppies or removable media (/media/name_of_media) you will still lack permission.  To mount the floppy in my case I have added a line to my ~/bashrc file in the alias section like this:-
alias floppy='sudo mount -t auto /dev/fd0 /home/andrew/Backup/Floppy'
Now to mount a floppy to that folder in my home I just have to type floppy in a terminal.

---

### Post by Thund3rstruck on 2006-07-04
If you're going to get a backup solution going you should go with rsync. It allows for network backups and the like and is real easy to use. It allows for incremental, full, differential backups, etc

---

