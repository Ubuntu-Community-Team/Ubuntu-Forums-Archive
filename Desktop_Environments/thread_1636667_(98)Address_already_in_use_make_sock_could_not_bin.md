---
title: "(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80"
date: 2010-12-03
forum: Desktop Environments
---

### Post by hhabashy on 2010-12-03
I would like to state first of all I am a novice with Linux, but have working in IT for 15 years.  I have been searching the web on this issue for almost 2 days (off and on:D), and have found that my particular issue was not the same as the norm for this particular error code.  I would like to give back (if you will).

Apparently having a cert.key password protected will hang Apache2 (maybe Apache as well).  The solution was to remove the password on the cert.key and that solved my problem.

The general consensus with resolving this issue did help me figure out that apache2 was running but waiting for password on boot-up. The following command which you will find everywhere out in the cloud is as follows:

sudo netstat -ltnp | grep ':80' (it is important to note that apache was hanging and it did not matter what port I decided to investigate)

This would return the following:
tcp6       0      0 :::80                   :::*                    LISTEN      1047/apache2    

Then I ran the following command:

sudo kill -9 1047 (the pid that appears on your particular instance)

I was able to restart Apache and everything was groovy until I rebooted.

I suspected the password and started researching the how to remove the passphrase off of the cert key and found the following article:

[http://www.mnxsolutions.com/apache/removing-a-passphrase-from-an-ssl-key.html](http://www.mnxsolutions.com/apache/removing-a-passphrase-from-an-ssl-key.html)

The following part of the page actually helped me:

Always backup the original key first (just in case)!

 # cp [www.key](www.key) [www.key.origThen](www.key.origThen) unencrypt the key with openssl. You’ll need the passphrase for the decryption process:

 # openssl rsa -in [www.key](www.key) -out new.keyNow copy the new.key to the [www.key](www.key) file and you’re done. Next time you restart the web server, it should not prompt you for the passphrase.

I hope this helps and saves someone some valuable time.

---

### Post by Xavi-avi on 2011-01-05
This is exactly what I was looking for.  Thanks!

---

### Post by lightsabersetc on 2011-01-06
You just saved me! Thank you!

---

### Post by vcrpcant on 2011-04-08
Thanks for taking the time to write this out, it helped me also :D

---

### Post by Krogen on 2011-08-21
Hate to bump an old thread, but this helped me.

Thanks a lot!

---

### Post by macns on 2012-02-06
I registered, just to reply to this thread, which saved me, thank you OP

Have to add though, after the kill command,  the apache start command might fail, with an error:
WARNING:  apache2 has already been started.
Do a apache 'zap', so you manually resetting apache's state to stopped.
Then, try apache start

EDIT: notice I killed the process twice!

Logs:
```

no listening sockets available, shutting down
Unable to open logs                                                       [ ok ]
ns1 ~ # netstat -ltnp | grep ':80'
tcp        0      0 :::80                   :::*                    LISTEN      3945/gpasswd        
ns1 ~ # kill -9 3945
ns1 ~ # /etc/init.d/apache2 restart
 * Stopping apache2 ...                                                   [ ok ]
 * Starting apache2 ...  
(98)Address already in use: make_sock: could not bind to address [::]:80
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs                                                       [ ok ]
ns1 ~ # netstat -ltnp | grep ':80'
tcp        0      0 :::80                   :::*                    LISTEN      4019/httpd          
ns1 ~ # kill -9 4019
ns1 ~ # netstat -ltnp | grep ':80'
ns1 ~ # /etc/init.d/apache2 start
 * WARNING:  apache2 has already been started.
ns1 ~ # /etc/init.d/apache2 zap
 * Manually resetting apache2 to stopped state.
ns1 ~ # /etc/init.d/apache2 start
 * Starting apache2 ...                                                     [ ok ]
ns1 ~ # 

```

Again. thanks OP, you're a lifesaver

---

### Post by Yourname on 2012-05-17
Thank you so much for this. 
It happened to me after running 'yum update' on an Elastix system (which relies on httpd GUI). And it wouldn't start.

But after removing ssl and rebooting, it worked. 
Thank you again!
(Hope my keywords help other Elastix users who stumble here)

---

### Post by Alpinist1974 on 2013-04-04
Thank you! This saved my ass during a server upgrade! Exactly what I needed, clearly explained.

---

### Post by oldos2er on 2013-04-04
Old thread closed.

---

