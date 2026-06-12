---
title: "Having errors when using rm on write protected files"
date: 2005-11-05
forum: Desktop Environments
---

### Post by eelozano on 2005-11-05
Techincally this isn't an Ubuntu problem (I am ssh'ing into my webserver).  These files were made by me (automated process by a web calendar i installed, but no root access).  Below is the exact output I got using rm with verbose output.

Note: Bold is the shell prompt

**-jailshell-2.05b$ rm -rv data**
rm: descend into write-protected directory `data'? y
rm: remove write-protected regular file `data/prefs.php'? y
rm: cannot remove `data/prefs.php': Permission denied
rm: remove write-protected regular file `data/200412060500pm.txt'? y
rm: cannot remove `data/200412060500pm.txt': Permission denied
rm: remove write-protected regular file `data/200412150200pm.txt'? y
rm: cannot remove `data/200412150200pm.txt': Permission denied


Any help is appreciated,

eelozano

---

### Post by matthew on 2005-11-05
try```
sudo rm -rv data
```but be careful and make sure you know what you are doing so you don't delete everything on your hard drive!

---

### Post by eelozano on 2005-11-05
**-jailshell-2.05b$ sudo rm -rv data**
sudo: can't stat /etc/sudoers: No such file or directory



seems that sudo doesn't exist on this particular comp?

---

### Post by matthew on 2005-11-05
Hmm. Okay. Assuming your user account is allowed root access using su you can
```
$ su
<password>
#
``` and voila, you have a root terminal (signified by the # prompt). Then you can do your maintenance.

Is the box you are connecting to running Ubuntu or something else?

If it is running Ubuntu, then sudo should be installed. In any case, if it is Ubuntu or Debian you can
```
# apt-get install sudo
``` and then put your user name in the sudoers file or make sure your user name is listed in the admin group (the second option is a bit easier)

I'm hesitant to say more about how to do this just because you can cause as much harm as good if you don't know what you are doing.

If you do not have admin/root privileges for this user you will need to contact whoever does and ask for help.

---

### Post by eelozano on 2005-11-05
Yeah it is a webserver that I pay to have access to.  I am just wondering how I made a write protected file (that I don't have permission to).  Granted the files were automated, but I figured that without having the permission I could not take it away from myself.

---

