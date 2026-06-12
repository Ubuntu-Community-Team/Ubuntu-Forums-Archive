---
title: "Permissions, Changing files other than home"
date: 2009-05-23
forum: General Help
---

### Post by Will Murray on 2009-05-23
I know this is a quite a newbie question but I can't find an answers anywhere.

How do I change permissions, so that I can change files that aren't in my own directory?

---

### Post by DeMus on 2009-05-23
> **Will Murray said:**
> I know this is a quite a newbie question but I can't find an answers anywhere.

How do I change permissions, so that I can change files that aren't in my own directory?

Open a terminal: Application - Accessories - terminal
It will open in your home folder with a command prompt:name@computername:~$
Now you have to move to the folder you want to change the files in:
cd foldername
Mind you this needs some explanation:
linux folders are organized top to bottom, top folder is "/' or root.
if you need to go to a folder abc in folder etc you type:
cd /etc/abc
(forward slashes not the windows backward slashes: remember linux goes forward, windows goes backwards)

To see the files and folders use:
ls -l
the -l option gives you the long list with details of each file and folder

Example:
jan@2-Quad:/tmp$ ls -l
total 28
srwxr-xr-x 1 jan jan    0 2009-05-23 06:46 gnome-system-monitor.jan.3504710957
drwx------ 2 jan jan 4096 2009-05-22 19:24 keyring-tuOMwz
drwx------ 2 jan jan 4096 2009-05-23 09:29 orbit-jan
drwx------ 2 jan jan 4096 2009-05-23 09:17 plugtmp
drwx------ 2 jan jan 4096 2009-05-22 19:24 pulse-d4jw37oo4ndp
drwx------ 2 jan jan 4096 2009-05-22 19:24 seahorse-imrelN
drwx------ 2 jan jan 4096 2009-05-22 19:24 ssh-OvUmJg3672
drwx------ 2 jan jan 4096 2009-05-22 19:24 virtual-jan.IQKSec

each line starts with 10 characters, in this case drwx------
d stands for directory (or folder), can be l for a link
the next 3 items "rwx" belong to you, the user and they state you have the right to Read, Write and eXecute the file or folder.
then the next 3 are for the group you belong to and can be dashes, or r,w,x also giving permission for the group to Read, Write or eXecute, or not when you see the dash.
The last 3 are for everybody else (called the world) and can be r,w,x and - also.

In my list I (user jan) own all files and folders in the example and I can do with it what I want.
Group jan can do nothing and so can do the world.

Change permissions: use chmod (change modus)
chmod +x  : make executable bit high so file can be executed
chmod 744 : gives you (user) total control (r,w,x = 4+2+1=7), group can read (r=4) and the world can read as well (r=4)

Mind you, when doing this on files and folders not owned by you, you need root permission, so the line would be:
sudo chmod +x (or 744, or whatever number you need)
(it will then ask for your password, not the root password)

Be careful doing this, because there is a reason why permissions are set the way they are set.

In which folder do you want to change something?

---

### Post by mcduck on 2009-05-23
Simple answer, you don't.

Changing permissions/ownerships of system files is a sure way to break your system.

If you need to access files/directories that require higher permissions than what you have, the solution is *not* changing those files/directories to require lower permissions, but instead change your own permissions. In Ubuntu this is usually done temporarily by using "sudo"-command.

You'd better read this: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

