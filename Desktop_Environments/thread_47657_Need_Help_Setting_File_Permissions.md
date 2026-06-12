---
title: "Need Help Setting File Permissions"
date: 2005-07-09
forum: Desktop Environments
---

### Post by Tad030 on 2005-07-09
I'm having problems setting the file permissions.  When I click on the properties button of any given file, this is what the filesystem properties screen says:

file owner: root
file group: root 

you are not the owner, so you can't change permissions 

I have read through the help guide for newbies, and I'm still lost.  Moreover, I *think* I've already made my accound the root user account, so I'm confused as to why this is happening.

---

### Post by adwait on 2005-07-09
It is recommended NEVER to use the root account for day to day uses, and hence Ubuntu out of the box, doesnt have a root account unless u create it later. Anyway, you can change the owner of any file using
sudo chwon <username> <filename> 
in the terminal.

---

### Post by tonym on 2005-07-09
"chown",  not "chwon"

---

### Post by Tad030 on 2005-07-09
This is what I typed in, and this is what happens

tad@Tad:~$ sudo chwon tad filesystem
Password:
sudo: chwon: command not found

---

### Post by Tad030 on 2005-07-09
maybe i'm asking the wrong question.  under places/computer/filesystem, all files are locked.  i can access files under my user directory just fine, but i'm confused as to why all the computer/filesystem files are locked, and why i cannot change the permissions on them.  i'm not trying to change any of the files or folders, but from what i have read, i think should be able to change permissions on these files, but i cant.

---

