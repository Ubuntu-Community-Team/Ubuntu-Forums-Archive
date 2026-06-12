---
title: "sudo corruption"
date: 2006-01-17
forum: General Help
---

### Post by jpfinley on 2006-01-17
During an install, I foolishly decided to **chown** a whole slew of folders, including /usr/bin . Now I fear that I have done something terrible; any use of sudo results in a nasty error.

Opening an application gives me```
Failed to run /usr/bin/some_application as user root:
Child terminated with 1 status
```

Command line sudo usage gives me```
john@aux:~$ sudo apt-get update
sudo: must be setuid root

```

I'm freaking out, afraid to log out or restart.  Any ideas?

---

### Post by RAOF on 2006-01-17
If you reboot into single user mode (in GRUB that's marked as "(recovery mode)"), you'll have root access and should be able to fix this.  Just re-chown the directories back to root (you won't have to use sudo to do this).

---

### Post by jpfinley on 2006-01-17
I appreciate the fast support.

I have followed your instructions and rebooted into recovery mode.  At the command line, I used the chown command recursively to set everything in the /usr/ folder back to root permissions (all of the subfolders now have that permission and read/write properties of 755).  I stll receive the error, however.

---

### Post by Ubuntuud on 2006-03-26
[QUOTE=RAOF]If you reboot into single user mode (in GRUB that's marked as "(recovery mode)"), you'll have root access and should be able to fix this.  Just re-chown the directories back to root (you won't have to use sudo to do this).[/QUOTE]

How do you re-chown directories?

---

### Post by Ramses de Norre on 2006-03-26
chown username path_to_file

---

### Post by Sutekh on 2006-03-26
[QUOTE=jpfinley]At the command line, I used the chown command recursively to set everything in the /usr/ folder back to root permissions (all of the subfolders now have that permission and read/write properties of 755). I stll receive the error, however.[/quote]
Those folders should be owned by root and have 755 permissions.

What commands did you use to change things back? And for that matter, what command specifically did you use when things went wrong?

I would think you need these commands
```
sudo chown -R root.root /usr/
sudo chmod -R 755 /usr/
```

[QUOTE=Ubuntuud]How do you re-chown directories?[/QUOTE]

You may also need the -R flag to allow the chown command to filter through all the sub-directories too.
```
chown **-R** owner.groupowner /<path of directories>
```
Will **ch**ange **own**nership of the directories to owner and the group ownership to groupowner.  You can leave out the .groupowner if you wish.

---

### Post by BLTicklemonster on 2006-09-05
I went into the recovery console (reboot, and chose recovery console in case you didn't catch on to how to do that), and typed 

ls -l usr/bin/sudo 

and the readout looked fine, like this 

```
-rwsr-xr-x 1 root root 93844 2006-05-17 08:41 /usr/bin/sudo
```

but I knew better...


so I put 

chwon root:root /usr/bin/sudo
then
chmod 4755 /usr/bin/sudo

then I typed 

reboot


and I now have sudo again.

---

