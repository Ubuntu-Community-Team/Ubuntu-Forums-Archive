---
title: "Request Help!!!"
date: 2006-02-25
forum: Desktop Environments
---

### Post by naveents on 2006-02-25
How do i get into administrator mode?? Right now..i am the only user!! But i am not having the prevelages of an administrator,like changing the read only status of some files.etc.. is there any root password?? I donot remember entering any root password while installing!!! Plz help!!!

---

### Post by taurus on 2006-02-25
Use sudo if you need to modify or install something on your system,

```

sudo <command>

```

---

### Post by aysiu on 2006-02-25
Read this:
[http://www.psychocats.net/linux/permissions.php](http://www.psychocats.net/linux/permissions.php)

---

### Post by drachir on 2006-02-25
I had the same problem with my install.  What root password? I didnt put one in! Why is linux looking me out of my own system.  Well linux isnt like that. Linux isnt like that, linux will never lock you out.  What I did was change my root password to something I knew and could remember. This is what I did
 Click System
 Click Administration
 Click Users and Groups
Enter your password that you used when you did your install. This is you log in password.
 Check *Show all users and groups* in the lower left section  
 click root
 Click properties
 in the lower end of the window you will find a place to place a root password manually. type in what you want and click OK.

now you can log in as *su* with a *root* password you know

Linux is very straight foward.

I hope this helps.

---

### Post by abhaysahai on 2006-02-26
on the terminal
sudo -s
<Password> 
now you are root, do whatever you like, did I mention that take proper caution and root can delete CRITICAL files and can cause permanent damage.

---

