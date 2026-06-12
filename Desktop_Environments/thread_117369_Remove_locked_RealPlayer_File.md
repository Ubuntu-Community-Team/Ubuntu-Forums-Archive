---
title: "Remove locked RealPlayer File ?"
date: 2006-01-14
forum: Desktop Environments
---

### Post by r4ik on 2006-01-14
Would somebody help me to remove this please ?
Keeps telling me no owner.
Any suggestions would very nice.
Thanks in advance !

After installation pffft gone.



/home/../Desktop/RealPlayer-10.0.6.776 (with a "beep" lock on it)

---

### Post by super on 2006-01-14
right-click on the file, select properties and change the permissions settings.

---

### Post by Mr_Grieves on 2006-01-14
If it tells you you're not the owner.. then you're not.

```

Check permissions of file:
ls -la /path/to/your_file

Check what groups your in:
groups

```

You may use 'sudo' to escalate your permissions.
```

For example, change owner of file:
sudo chown user file

Change group ownership of file:
sudo chgrp group file

or just:
sudo rm file

```

---

### Post by r4ik on 2006-01-14
It didnt alow me to what i did is install it and it was gone.
Thanks for youre reply.

---

### Post by r4ik on 2006-01-14
[QUOTE=Mr_Grieves]If it tells you you're not the owner.. then you're not.

```

Check permissions of file:
ls -la /path/to/your_file

Check what groups your in:
groups

```

You may use 'sudo' to escalate your permissions.
```

For example, change owner of file:
sudo chown user file

Change group ownership of file:
sudo chgrp group file

or just:
sudo rm file

```[/QUOTE]

Here's my groups output doesnt tell me much..
There is a lot of new stuff in your reply may be usefull next time.
thanks !

r4ik@ubuntu:~$ groups
r4ik adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin
r4ik@ubuntu:~$

---

### Post by Mr_Grieves on 2006-01-14
Here's some good read for you:

[http://www.unixcities.com/howto/index3.html](http://www.unixcities.com/howto/index3.html)

You may also use 'chmod' to change permissions on a file.
Be aware of that changing permissions on files may lead to security problems in your system. So be careful.

---

### Post by r4ik on 2006-01-14
Bookmarked it thanks!
Gonna read it later with a clearer view :)

---

