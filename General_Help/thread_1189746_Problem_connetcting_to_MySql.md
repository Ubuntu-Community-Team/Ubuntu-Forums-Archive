---
title: "Problem connetcting to MySql"
date: 2009-06-17
forum: General Help
---

### Post by LgLindstrom on 2009-06-17
Hi
I've installed ubunto Server edition on as a LAMP server. After that I installed myPhpAdmin.
Following the instructions I found on this site, I downloaded Joomla and started to install it.
From another machine in my network, i created I new database on my server, using myPhpAdmin. From the same computer I started to configure Jomla following their step by step wizard. It all went well until the the wizard tried to connect to mysql. I got the message that it could not connect.

What can be wrong? The only difference I can see, from all other tutorial/examples I found on Internet is that am using a remote machine,, not localhost.

I am a newbe on this, so Im hoping for some help.

//lasse

---

### Post by cariboo on 2009-06-17
Use the user you setup when you installed mysql. Make sure you have the user setup properly by opening an Applications-->Accessories-->Terminal and type:

```
mysql -u root -p
```

enter the password you created when you installed mysql, you should get something that looks like this:

```
mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 28
Server version: 5.0.75-0ubuntu10 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql>
```

---

### Post by rohitfeb14 on 2009-06-17
Uninstalling and installing helped me

---

### Post by LgLindstrom on 2009-06-17
> **cariboo907 said:**
> Use the user you setup when you installed mysql. Make sure you have the user setup properly by opening an Applications-->Accessories-->Terminal and type:

```
mysql -u root -p
```

enter the password you created when you installed mysql, you should get something that looks like this:

```
mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 28
Server version: 5.0.75-0ubuntu10 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql>
```


I've done that. The only difference I can see on my setup, is connection id, my is 36.

Is there some problems with Firewalls. On my client computer I've tried to disable the firewall,,, but it makes no difference.

//lasse

---

### Post by LgLindstrom on 2009-06-17
> **rohitfeb14 said:**
> Uninstalling and installing helped me

What kind of "un-install",,, I've done almost every step manual,, how do I uninstall?

//lasse

---

