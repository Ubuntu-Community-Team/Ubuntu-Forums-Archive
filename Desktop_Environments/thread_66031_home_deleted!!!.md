---
title: "/home deleted!!!"
date: 2005-09-15
forum: Desktop Environments
---

### Post by Micho523 on 2005-09-15
Well i got a bug in me and decided to try out real player for linux. The install goes well, until it hit an error, and deleted all the install files. I set the install directory to /home. It not only deleted the install files, it deleted all directories to which it installed, so that means /home and its subdirectories are gone  ](*,) 

The only way i can log on is with the failsafe terminal.

If there is a way to fix this little dilemma without reinstalling, please let me know!!
Thanks!

---

### Post by Glut on 2005-09-15
try from root /:
mkdir /home
mkdir /home/username
cp /etc/skel/.* /home/username

where username is your username. Should get you out of trouble.


*Edit*
You will also need to:
chown -R username:username /home/username

Depending on your setup you may want to disable other's access to your home:
chmod og-rx /home/username

*I think that's everything now*

---

### Post by Micho523 on 2005-09-15
[QUOTE=Glut]try from root /:
mkdir /home
mkdir /home/username
cp /etc/skel/.* /home/username

where username is your username. Should get you out of trouble.


*Edit*
You will also need to:
chown -R username:username /home/username

Depending on your setup you may want to disable other's access to your home:
chmod og-rx /home/username

*I think that's everything now*[/QUOTE]
 Thanks a bunch Glut, that worked great! Turned out just /username got deleted. All I had to redo was remap my media keys!

---

