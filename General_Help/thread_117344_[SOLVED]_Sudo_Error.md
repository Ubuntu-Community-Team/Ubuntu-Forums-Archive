---
title: "[SOLVED] Sudo Error"
date: 2006-01-14
forum: General Help
---

### Post by Norwal on 2006-01-14
Hello all,

I've caused my self a small nightmare.  It all began when I thought I would change my computer's name. I read a post and followed it with great success. I managed to change the etc/hostname file and all seemed fine. 

Today I log on for the first time after the change and this error shows up:

>  Could not look up internet address for NorLinux.
This will prevent GNOME from operating correctly.
It may be possible to correct the problem by adding
NorLinux to the file /etc/hosts.

After looking around the forum again I found that the indeed the ./etc/hosts file needed to be edited aswell.  There in lies the problem. I can't access the files to edited them. Not from Terminal/Konsole nor in Recovery Mode. In each case I get the following error message:

> sudo: unable to lookup NorLinux via gethostbyname()


This occurs for all commands when sudo is used.  I type in just sudo and recieved the error message.

NorLinux is the new hostname. I can view the files but can't make any changes.

Short of a re-install is there any way around this problem.

---

### Post by Norwal on 2006-01-14
Found the answer at :

[http://www.ubuntuforums.org/showthread.php?t=117019&highlight=sudo%3A+unable+lookup](http://www.ubuntuforums.org/showthread.php?t=117019&highlight=sudo%3A+unable+lookup)

I used the nano command in Recovery Mode and I was able to edit the hosts file.:razz:

---

