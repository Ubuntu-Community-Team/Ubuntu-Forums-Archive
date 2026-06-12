---
title: "Help"
date: 2005-07-23
forum: Desktop Environments
---

### Post by Mastertronic on 2005-07-23
Hello..

Here is my quesion if anyone would like to answer them
I am a beginer using linux ubuntu. so here goes..

1. I cannot move files or delete folders etc, becouse the system is telling me I do not have permission to do so..now im using File Manager in Ubuntu and i prefer using that then terminal. and i know you have to type SUDO or something in terminal to get pass etc.. is there a way that i can just login in ubuntu just like Redhat 9 i use to have and just enter it as a root user. so i can just do whatever i gotta do?

This is me on ubuntu >  ](*,)  I cant log in as a Root user > \\:D/

---

### Post by kori.mendocino on 2005-07-23
[http://ubuntuforums.org/showthread.php?t=31053&highlight=enable+root+user](http://ubuntuforums.org/showthread.php?t=31053&highlight=enable+root+user)

---

### Post by timetunnel on 2005-07-23
The root account is disabled on ubuntu by default. That's different from other distributions. Therefore you can' t login as root. Read here about it (it also tells you how to enable it): [Root on ubuntu](https://wiki.ubuntu.com/RootSudo) 

Keep in mind that it can be dangerous to activate the root account and login to GNOME/KDE as root. You are god on that system then and can destroy you system by moving, copying or deleting  the wrong files. Though it seems quite uncomfortable in the first run, you'll get used to sudo quite soon (well, I got it at least). You can also do "sudo nautilus", which only starts the file manager as root, and not everything.
What kind of files do you want to move/copy? If they are your documents, mp3s or whatever, they should not be in a folder that only root has access to. Then your problem is not the root account but the user rights on certain files or folders on your system. Change these instead of risking your system then.

Jens

---

