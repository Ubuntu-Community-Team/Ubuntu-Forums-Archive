---
title: "add user???"
date: 2006-08-18
forum: Desktop Environments
---

### Post by afbase on 2006-08-18
i'm trying to add a user with access to proftpd.  How can I do this in CLI?

---

### Post by taurus on 2006-08-18
```

sudo useradd -m -g proftpd -s /bin/bash john
sudo passwd john

```

---

### Post by afbase on 2006-08-18
Grrr i have an unknown user group proftpd... how can I fix this?

---

### Post by murataht on 2006-08-18
1)
for add a new user try adduser command:
```
sudo adduser pftpuser
```

2) (i am not sure, if there is a proftp group. double check this one, or someone else could help here.)

and edit /etc/group , add this user to proftp usergroup.

or other suggestions from others

---

### Post by taurus on 2006-08-18
Do you have group proftpd in /etc/group?  

```
more /etc/group
```

---

### Post by afbase on 2006-08-18
No i don't have a proftpd group 
So now what?

---

### Post by taurus on 2006-08-18
Then I don't understand your original message then!  You want to create a new user that can control proftpd!  Have you installed proftpd on your machine and wh is the owner and group for proftpd then?

---

### Post by afbase on 2006-08-18
ya i have proftpd on my system,i'm not exactly sure about the owner and group for proftpd thing.  *sigh* ummmm how can I find that out?

---

### Post by taurus on 2006-08-18
Assuming you installed proftpd in /usr/bin, type this at the prompt...

```
ls -la /usr/bin/proftpd
```
The first name is the owner and the second is the group...

---

### Post by afbase on 2006-08-18
```
 ls -la /usr/bin/proftpd
ls: /usr/bin/proftpd: No such file or directory

```

however... i can restart proftpd when I
```
/etc/init.d/proftpd restart
Restarting ProFTPD ftp daemon.proftpd
..proftpd
 done


```

---

### Post by taurus on 2006-08-18
Then proftpd is not in /usr/bin.  Perhaps it's in /sbin.  Type this at the prompt and see what is the whole path tp proftpd.

```
whereis proftpd
```
Assuming it says /sbin/proftpd, then do

```
ls -la /sbin/proftpd
```

---

### Post by afbase on 2006-08-18
```

root@Condor:/home/clinton# ls -la /usr/sbin/proftpd
-rwxr-xr-x 1 root root 787004 2006-04-06 08:57 /usr/sbin/proftpd
root@Condor:/home/clinton#

```

---

### Post by taurus on 2006-08-18
Then proftpd is owned by root and group is also root then.  So if you want to control it, you have to be root!!!

---

### Post by afbase on 2006-08-18
okay so that means if i want a user to use proftpd, he/she has to be root??? if thats the case then how the heck do i change the owner and group.

---

### Post by scxtt on 2006-08-18
no, it's also readable and executable by anyone in the root group and "other" ...

---

### Post by afbase on 2006-08-18
so then how does one change change a user to the root group

---

### Post by taurus on 2006-08-18
What exactly do you want to do with proftpd?  Right now, root (owner) can read, write, and execute it while group (also root) can read and execute it and everybody else on your system can read and execute it...

---

### Post by scxtt on 2006-08-18
you don't need to do that ...

but if you want to change group properties of a file you can do:
[indent]chgrp <group_name> file
[center]or[/center]
chown <user_name>:<group_name> file[/indent]but as it stands, proftpd can be used by anyone ...

---

