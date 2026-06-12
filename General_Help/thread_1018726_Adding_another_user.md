---
title: "Adding another user"
date: 2008-12-22
forum: General Help
---

### Post by scratman on 2008-12-22
Hi guys.    I would like to know how I can add another user to my system.  The thing is, I want them to be able to access my external hard drive, and certain areas of the internal hard drive, as well as the internet, however, I want to keep my Home folder invisible.  I have set up a user account as guest, and my external HDD is mounted to /media/HD-CEU2

Any help gratefully received guys!

---

### Post by taurus on 2008-12-22
If you don't want someone to look in your $HOME, just change the permissions.

```
chown 700 /home/your_login_name
```
And if you want to create another user, look in System -> Administration -> Users & Groups.

---

### Post by scratman on 2008-12-22
That borked my machine, made my home folder and .dmrc inaccessible.  I had to log into Ubuntu at Terminal and chmod back to log into here again.

---

### Post by taurus on 2008-12-22
What do you mean it borked your machine?  What was the exact command that you ran?  

I have that permissions on my account and it has been running fine since Intrepid came out.

---

### Post by scratman on 2008-12-22
chown 700 /home/my_login_name

Made it so I couldn't access my home folder, and the .dmrc file appeared to be missing.  I managed to reset my permissions, but have made no progress towards my original aim.  Thanks for the assistance though, even if it does not appear to have worked on my machine.

---

### Post by taurus on 2008-12-22
What is your login name and what is the output of this command?

```
ls -la /home
```

---

### Post by scratman on 2008-12-22
andrew and

```
andrew@andrew-desktop:~$ ls -la /home
total 16
drwxr-xr-x  4 root   root   4096 2008-12-22 15:48 .
drwxr-xr-x 22 root   root   4096 2008-12-22 18:52 ..
drwx------ 87 andrew andrew 4096 2008-12-22 20:13 andrew
drwxr-xr-x 29 guest  guest  4096 2008-12-22 19:08 guest

```

---

### Post by taurus on 2008-12-22
> **scratman said:**
> andrew and

```
andrew@andrew-desktop:~$ ls -la /home
total 16
drwxr-xr-x  4 root   root   4096 2008-12-22 15:48 .
drwxr-xr-x 22 root   root   4096 2008-12-22 18:52 ..
**[COLOR="Blue"]drwx------[/COLOR]** 87 andrew andrew 4096 2008-12-22 20:13 andrew
drwxr-xr-x 29 guest  guest  4096 2008-12-22 19:08 guest

```

So what is the problem then?

---

### Post by scratman on 2008-12-28
Hi Taurus.

Currently there is no problem, but this is because I have managed to fix it.  My system was telling me that I did not have the correct permissions to access my home folder.  I could log in, but was presented by a blank orange screen.  I could, however, log into the terminal and revert my permissions, enabling me to get up and running again.  I am sure that the advice you gave was in good faith, however, it appears that my system did not like it.

The original issue still has not been resolved.  Is there any graphical way to allow selective permissions to users?

---

