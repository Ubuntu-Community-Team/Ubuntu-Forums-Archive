---
title: "Permissions broken after running sbackup. Please help!"
date: 2006-09-24
forum: Desktop Environments
---

### Post by aNoble on 2006-09-24
I don't know what happened but something is very messed up.

I heard about SBackup and installed it. I couldn't get the smb:// or ftp:// connection to work so I backed up locally to /home/anoble/Backup/. I click Run Backup and almost immediatly Gnome starts to crash little by little (services stop, icons and wallpaper go blank, etc.). I switch to a terminal and try to login with my account and can't so I login as root and shutdown the computer.

Now I can't login as anybody but root. Here's what I'm getting with different commands. 

```
$su - anoble
Unable to cd to "/home/anoble"
```

```
$su anoble
No shell
```

Trying to start gdm fails. I can run startx as root but only some things work (networking is dead but that may just be a dhcp problem). I can't find any missing files from the backup and all of the permissions seem fine. I tred creating a new user but I get the same results. It seems like anything that is not run as root does not work. I'm also seeing a few errors about dbus which might be part of the problem. Also I couldn't find anything in the logs other than some permission denied errors.

Any help would be greatly appreciated. If I can't get this fixed I'm going to have reinstall from scratch.

---

### Post by aNoble on 2006-09-24
Nevermind.

I figured it out. Somehow / permissions got set to 700. I set them back to 755 and everything is fine.

---

### Post by aNoble on 2006-09-24
Just a quick update for anyone who may be having the same problem or is considering using Simple Backup.

I installed [version 0.10]("http://sourceforge.net/project/showfiles.php?group_id=145360&package_id=159869&release_id=441298") instead of 0.9 (which is in the repository) and everything seems to be working fine. It will now backup to a smb:// share and no more clazy root permission problems (although that might be because I'm not backing up locally). Also, there is a new purge option which seems very nice.

---

### Post by veebis on 2006-10-30
How did you get a Samba share to be your destination?
I just set up the latest (10.3) and am unable to get this to work... :confused: 
Thanks!
-Vb

---

