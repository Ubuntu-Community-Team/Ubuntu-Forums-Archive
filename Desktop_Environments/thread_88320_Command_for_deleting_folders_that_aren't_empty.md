---
title: "Command for deleting folders that aren't empty?"
date: 2005-11-10
forum: Desktop Environments
---

### Post by EnderTheThird on 2005-11-10
Is there a command that I can use in the terminal that will remove a folder/directory that isn't empty?  Whenever I try to use "rmdir" it complains that the directory isn't empty.  The reason I ask is that I want to install Ubuntu on a lobby computer at work (a hotel) for guests to use, so I'd like to create a script for deleting all the files in the user's home directory and then untar a pre-created set of folders/files to the newly created home directory.  Thanks.

---

### Post by RAOF on 2005-11-10
rm -r is a recursive delete - it will delete all the files in a folder, then delete the folder.

---

### Post by Ufo on 2005-11-10
If I remember correctly using
rm -dr
will remove directory and its contents in one command, using
rm -drv
gives output what has been removed.

---

### Post by kagashe on 2005-11-10
try
rm -rf

kagashe

---

### Post by EnderTheThird on 2005-11-10
I can't try it out at the moment because I'm at school, but I'm sure at least one of those will work, thanks.  Now if only I could find out where to put the script so it can be run automagically every time the guest user logs in and/or logs out so I don't need to explain to the other people at work how to type one command into a terminal.

---

### Post by Mizzou_Engineer on 2005-11-10
Well, you can put it in /etc/init.d if you want it to execute it at every boot-up, you can put it in the startup services folder if you want it to execute at that user's login. In KDE, it is at /home/*user*/.kde/Autorun. I don't know where it is in Gnome, sorry, I am an ex-KDE user who's kind of new to Gnome. But I do know there is one.

---

### Post by RAOF on 2005-11-10
[QUOTE=EnderTheThird]I can't try it out at the moment because I'm at school, but I'm sure at least one of those will work, thanks.  Now if only I could find out where to put the script so it can be run automagically every time the guest user logs in and/or logs out so I don't need to explain to the other people at work how to type one command into a terminal.[/QUOTE]
If they're logging in to Gnome, you could add the script to the session:
System->Preferences->Session, and it will be run each time they (that user) login to Gnome.

---

