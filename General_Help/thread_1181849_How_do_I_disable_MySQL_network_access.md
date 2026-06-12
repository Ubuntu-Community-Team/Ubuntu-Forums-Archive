---
title: "How do I disable MySQL network access?"
date: 2009-06-08
forum: General Help
---

### Post by lorderico on 2009-06-08
I have an installation of Moodle running on an Ubuntu 8.04 server.  One of the security recommendations on the Moodle Docs website is "turn off network access to MySQL".  How do I do this?  Also, will it impact anything?  I am under the impression that MySQL is never accessed remotely.

Eric

---

### Post by Celauran on 2009-06-08
I believe that's done by default. Check your /etc/mysql/my.cnf and you should see the following:

```
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address            = 127.0.0.1
```

---

### Post by lorderico on 2009-06-08
> 
```

# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address            = 127.0.0.1

```


Yes, those line exist.  How come when I run netstat -a, the first line is:

```

Proto Recv-Q Send-Q Local Address   Foreign Address State
tcp   0      0      localhost:mysql *:*             LISTEN

```

Does that indicate that network access is possible?

Eric

---

### Post by bjk03 on 2009-06-08
With bind-address set to localhost, only applications that run on the same machine as mysql can access mysql.

---

### Post by cariboo on 2009-06-08
By default mysql is setup not to have network access. To check, mysql runs on port 3306, go to System Administration-->Network Tools-->Port Scan, type localhost in the Network Address bar and click the scan button. If you don't see port 3306 in the list, then mysql is not accessable from the network.

---

### Post by lorderico on 2009-06-08
I used the command nmap instead because I am working with Ubuntu server and I don't have a gui.  I ran the command 

nmap 127.0.0.1

with this result:
```

Not shown: 1712 closed ports
PORT     STATE  SERVICE
80/tcp   open   http
3306/tcp open   mysql

```

Doesn't that mean that it is available for network access?

Eric

---

### Post by cariboo on 2009-06-08
Yes, mysql is accessible from the network. What mysql config file are you using? My setup uses /etc/mysql/my.cnf.

THe way I usually setup network access to mysql is create a user that can remotely access it using the following commands:

```
grant all privileges on *.* to <user>@'localhost' identified by '<password>' with grant option
```

the above command give the user local access

```
grant all privileges on *.* to <user>@'%' identified by '<password>' with grant option
```

enables the <user> remote access.

---

