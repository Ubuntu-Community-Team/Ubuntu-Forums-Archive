---
title: "SSH Daemon"
date: 2009-01-16
forum: General Help
---

### Post by theQmaster on 2009-01-16
How do I get SSH daemon to tell me the status ? Without looking thru it's logs ?

When I do /etc/init.d/ssh restart there no response from it...

Thanks!
Q

---

### Post by taurus on 2009-01-16
ssh is a client.  You mean /etc/init.d/sshd.

---

### Post by albinootje on 2009-01-16
> **theQmaster said:**
> How do I get SSH daemon to tell me the status ? Without looking thru it's logs ?

When I do /etc/init.d/ssh restart there no response from it...


Try this instead :

```

sudo /etc/init.d/ssh restart

 * Restarting OpenBSD Secure Shell server sshd   [ OK ] 

```

---

### Post by pocketchange on 2009-01-16
If all you want is the status, you can run "sudo /etc/init.d/ssh status" and it should report whether sshd is running.

---

### Post by albinootje on 2009-01-16
> **pocketchange said:**
> If all you want is the status, you can run "sudo /etc/init.d/ssh status" and it should report whether sshd is running.

Alas..
> 
$ sudo /etc/init.d/ssh status
 * Usage: /etc/init.d/ssh {start|stop|reload|force-reload|restart|try-restart}


This is an option :
> 
$ ps auxw|grep ssh
root     15729  0.0  0.0   5316   988 ?        Ss   22:18   0:00 /usr/sbin/sshd
adriaan     16034  0.0  0.0   3004   768 pts/2    R+   22:35   0:00 grep ssh


---

### Post by pocketchange on 2009-01-16
I guess you could just try to kill the running process.  I'm not sure which version of the openssh-server package you have, but here's mine:

```
% dpkg-query -l 'openssh-server*' 
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                   Version                                Description
+++-======================================-============================
ii  openssh-server                         1:5.1p1-3ubuntu1                       secure shell server, an rshd replacement
```

I'm not quite sure why your package has no status option in the init.d script.

---

### Post by theQmaster on 2009-01-16
All good idea...

Just to meantion that it worked fine in 6.06 it stopped working after moving to Gutsy!

---

### Post by theQmaster on 2009-01-16
> **taurus said:**
> ssh is a client.  You mean /etc/init.d/sshd.

there is no sshd!

---

### Post by albinootje on 2009-01-16
> **theQmaster said:**
> there is no sshd!

In Ubuntu and Debian there's /etc/init.d/apache or /etc/init.d/apache2 while in RedHat based or alikes it's /etc/init.d/httpd since years.
It's all about confusing us in the end, we, the users .. :)

---

