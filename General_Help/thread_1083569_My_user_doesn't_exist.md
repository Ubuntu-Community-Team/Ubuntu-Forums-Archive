---
title: "My user doesn't exist"
date: 2009-03-01
forum: General Help
---

### Post by Nonc on 2009-03-01
Hey, so im trying to get usb devices to work in virtual box.

did some searching and found this [http://www.linuxquestions.org/questi...ything-572446/](http://www.linuxquestions.org/questi...ything-572446/) which will probably work.

problem is, when i go into System>Administration>Users & Groups only the root user shows up. As if my username doesnt exist. It could be because of the funny way i moved my home drive from one partition to another, or something.

but either way, i cant complete the rest of the instructions until my username shows up on there.

Im running Ubuntu 8.10, and everything else works fine. I log in, i log out no problem. Oh, and there is only one user - me.

ive checked /etc/passwd and i am there

user:x:501:501:Real Name,,,:/home/user:/bin/bash

with the correct user name and Real name in it

and ls -l does say that i own the folders.

like i say, ive never met another problem saying there isnt a user, only i am not listed in the users and groups thing. There is a group named after me, but nobody is a member of it, and i cant add myself to it.

How do i solve this?

Cheers

nonc

ps cross posted at [http://www.linuxquestions.org/questions/linux-software-2/i-am-not-a-user-707403/](http://www.linuxquestions.org/questions/linux-software-2/i-am-not-a-user-707403/)

---

### Post by Xiong Chiamiov on 2009-03-01
Your first link needs to be edited, since it got truncated when you copy+pasted.

You can add a user to a (secondary) group with the command
```

sudo usermod -a -G [group] [user]

```

---

### Post by heindsight on 2009-03-01
I believe the reason you're not being listed in the 'Users & Groups' dialog is because your UID is 501. Ubuntu tends to consider UID's less than 1000 to belong to system accounts (ie. accounts created for various system services - eg the system logger runs as user syslog, etc). The 'Users & Groups' dialog only lists the root account and user accounts (with UIDs >= 1000) because you should never need to change any of the system accounts.

I'm not sure how you ended up with a UID of 501, maybe it has something to do with "the funny way" you moved your home onto a new drive, another possibility is that you're using a passwd file originally created on another distro. 

Anyway I would not recommend you try to change your UID, the only changes you should ever need to make to your account are to occasionally add yourself to a new group, and for that it's easy enough to use the usermod command.


If you really do want yourself to show up in 'Users & Groups', you can boot into recovery mode (just safer that way) and do:
```
usermod -u 1000 yourusername
groupmod -g 1000 yourusername
find / \( -uid 501 -exec chown +1000 \{\} \; \) -o \( -gid 501 -exec chgrp +1000 \{\} \; \)
``` 
the usermod command will change your UID to 1000 (and also change the UID's of any files you own in your home directory to 1000). the groupmod command will change the GID of your login group (the group with the same name as your username) to 1000, but it won't change any files. The find command will find any remaining files on the system with UID 501 and change their UID to 1000 as well as any files with GID 501 and change their GID to 1000.

---

### Post by Nonc on 2009-03-02
Worked brilliantly. Thank you very much heindsight

---

### Post by heindsight on 2009-03-02
It occurs to me that if you've ever used nautilus to delete files from partitions other than your home partition or from any removable media, then those partitions and removable media may contain hidden trash directories with names constructed using your old UID.

You may want to search for those and rename them. Perhaps try something like:
```
sudo find / -name ".Trash-501" -exec rename s/Trash-501/Trash-1000/ \{\} \;
```
Or simply delete them:
```
sudo find / -name ".Trash-501" -prune -ok rm -R \{\} \;
```
(the -ok instead of -exec means you'll be asked before each directory is removed)

---

