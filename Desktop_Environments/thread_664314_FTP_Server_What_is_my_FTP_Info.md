---
title: "FTP Server What is my FTP Info ?"
date: 2008-01-11
forum: Desktop Environments
---

### Post by dontgetshocked on 2008-01-11
Ok, I am new at this for sure.I installed vsftpwith no errors but now how do I allow my sister access to my FTP folder on my pc? I want to use a username and password of course.I shared the FTP folder already.What else step by step  PLEASE do I need to do to make this work?

P.S. I did try to solve this on my own and also a search via this forum  with no luck,

Dave

---

### Post by nexu56 on 2008-01-16
You can run the following commands from the terminal.

Install vsftpd:
```

sudo apt-get install vsftpd
```

Edit the config file to disable anonymous access:

```
gksudo gedit /etc/vsftpd.conf
```

Find the bit where is says "anonymous_enable=YES" and change to "anonymous_enable=NO" 
Find the bit where is says "local_enable=NO" and change to ""local_enable=YES"

Restart vsftpd for changes to take effect

```
sudo /etc/init.d/vsftpd restart
```

You should now be able to log in to your own home directory via FTP if you connect to address "localhost", with your usual account details.

If you want to create an account for your sister:

```
sudo adduser mysister
```

Her FTP directory is located in /home/mysister.

cheers,

nexu56

---

