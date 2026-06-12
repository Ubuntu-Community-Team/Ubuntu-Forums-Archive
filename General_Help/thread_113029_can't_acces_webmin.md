---
title: "can't acces webmin"
date: 2006-01-05
forum: General Help
---

### Post by cotn on 2006-01-05
A few days ago I installed webmin_1.180-2 as follows;

```
sudo apt-get --purge install  webmin
```

That worked fine and I was able to reach the server at 
[http://127.0.0.1:10000](http://127.0.0.1:10000)

But when I tried to login the app with root and its password, I get the message "Login failed. Please try again". 
After three times it secures itself to block al access for 300 seconds. True its save but if I  cant even Login...

Then I tried: 

```
sudo /usr/share/webmin/changepass.pl /etc/webmin root xxxxxxx
```
With ubuntu root pwd ofcourse.

Okay he had no problems with that, but when I tried to login again, the same login failure messages where printed on the screen.

ok: then I changed my root pwd with: 

```
sudo passwd root
```

and again:

```
sudo /usr/share/webmin/changepass.pl /etc/webmin root xxxxxxx
```

Still no good.

Then I did a complete removal, for a fresh new installation. But then he slaps me with the message:

```
stopping webmin. start-stop-daemon: warning failed to kill 8478 No such processes
```  

So fine, what do I care, just truncate it.

But when I did a new purged install I received the errors:

```

sudo: cannot get working directory

blablabla... and:

After unpacking 6050kB of additional disk space will be used.
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory

Preconfiguring packages ...
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory

blablabla again... and:

miniserv.pem: No such file or directory
Starting webmin: webmin.

```

So Now I'm back to start! I can reach the server but still no good.

Can someone please help me out here, google gave up on me also.

Thanks in advance

---

### Post by cotn on 2006-01-07
somebody ?

---

### Post by orliville on 2006-01-13
I'm having the same issue, any help would be appreciated.

---

### Post by nycjuni on 2006-01-13
Try this..
:rolleyes: 

1- Login on local workstation [http://127.0.0.1:10000](http://127.0.0.1:10000)
2- Enter username root and your password
3- Select Webmin configuration
4- Select IP access control and enter your network ip ex,,192.168.1.0

---

### Post by cotn on 2006-01-14
[QUOTE=nycjuni]Try this..
:rolleyes: 

1- Login on local workstation [http://127.0.0.1:10000](http://127.0.0.1:10000)
2- Enter username root and your password
3- Select Webmin configuration
4- Select IP access control and enter your network ip ex,,192.168.1.0[/QUOTE]

Well it ends by step 2. That's the whole issue here. I just can't login. So I'm not bothering about network ip's right now. I deal with that when I have acces to the app. 

Thanks for youre reply though

---

### Post by cotn on 2006-01-26
But still no one else that can help me out here ? :(

---

### Post by matpaa on 2006-01-27
Ok, i'm newbie with Linux, so i don't know everything, but ...

I had same problem just 10 minutes ago and this is how i solve my problem:

first i stoped webmin service
   sudo sh /etc/webmin/stop

then i started again ... somebody would know better way to do this, but it works ;)
   sudo sh /etc/webmin/start

then i set root password for webmin
   sudo perl /usr/share/webmin/changepass.pl /etc/webmin root newpassword

... and that's it ... that worked for me.

---

### Post by gronbaek on 2006-01-28
Hi

I had exactly the same problem and found the answer in this thread: [http://ubuntuforums.org/showthread.php?t=120939&highlight=webmin](http://ubuntuforums.org/showthread.php?t=120939&highlight=webmin)

But i had to remove/purge webmin to get it to work, and then reinstall.

---

### Post by cotn on 2006-01-30
Gronbaek, thanks for giving the final hint to fix this problem. It worked out and I can finaly acces webmin. I did not have to remove webmin. Just /etc/webmin/stop and append the giving lines was enough to get everything to work.

So I'm very thankfull to you and everyone else participating this thread.

final url: [https://wiki.ubuntu.com/WebminWithoutARootAccount](https://wiki.ubuntu.com/WebminWithoutARootAccount)

---

### Post by seekyrr on 2006-01-31
[QUOTE=matpaa]Ok, i'm newbie with Linux, so i don't know everything, but ...

I had same problem just 10 minutes ago and this is how i solve my problem:

first i stoped webmin service
   sudo sh /etc/webmin/stop

then i started again ... somebody would know better way to do this, but it works ;)
   sudo sh /etc/webmin/start

then i set root password for webmin
   sudo perl /usr/share/webmin/changepass.pl /etc/webmin root newpassword

... and that's it ... that worked for me.[/QUOTE]

This solved my problem..Thanks!  Was going a little nutz on this one

---

