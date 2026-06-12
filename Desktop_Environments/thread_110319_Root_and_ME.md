---
title: "Root? and ME?"
date: 2005-12-30
forum: Desktop Environments
---

### Post by s_spiff on 2005-12-30
Hey, I just installed Ubuntu BB about 15 minutes back, to configure my net [ LAN] I need to install a package rp-pppoe, which i have on a cd. I have to extract it on usr/src something something [ sorry, but I'm new to linux, and don't remember the exact path ] . Now Everytime I try to extract the files of that zip like folder, I get an error that I do not have the permission to extract in the src folder. I'm logged on my own account, there being only one user for the system, i.e. me. Anyways, I hope this can help you help me, forgive my vagueness. Also, where exactly can I learn online about linux, or specifically Ubuntu? I really have no clue as to what I'll be doing on it. I only hope that soon enough I'll shift from MS to Linux.

---

### Post by kaamos on 2005-12-30
You can start the file manager as root (with more permissions) by using this command in terminal
```
sudo nautilus
```
And give your password.

You don't by default have write access except in your home directory (/home/**username**), and you can use the sudo command to perform operations elsewhere.

Try looking here:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://en.wikipedia.org/wiki/Superuser](http://en.wikipedia.org/wiki/Superuser)

---

### Post by tagg3rx on 2005-12-30
from the terminal type 

pppoeconf

follow the prompts - it should get you online

--your new to ubuntu the first thing you should learn is its much easier than it seems you dont need to realy go out and download and install anything.

Check out automatix (see the custimation board theres a sticky)
and check out symantec - it lists every app you can install in ubuntu


Enjoy

---

### Post by homegrown on 2005-12-30
Hey there, the post above will do the trick, but is in the longrun you should get to know Linux file permissions. 


pin this up next to your PC & you'll be up & running in no time.

remember to sudo if you're not root!

chmod 400 file	To protect a file against accidental overwriting.
chmod 500 directory	To protect yourself from accidentally removing, renaming or moving files from this directory.
chmod 600 file	A private file only changeable by the user who entered this command.
chmod 644 file	A publicly readable file that can only be changed by the issuing user.
chmod 660 file	Users belonging to your group can change this files, others don't have any access to it at all.
chmod 700 file	Protects a file against any access from other users, while the issuing user still has full access.
chmod 755 directory	For files that should be readable and executable by others, but only changeable by the issuing user.
chmod 775 file	Standard file sharing mode for a group.
chmod 777 file	Everybody can do everything to this file.

---

