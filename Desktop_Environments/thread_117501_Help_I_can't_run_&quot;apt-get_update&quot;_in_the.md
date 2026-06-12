---
title: "Help: I can't run &quot;apt-get update&quot; in the terminal"
date: 2006-01-15
forum: Desktop Environments
---

### Post by kenweill on 2006-01-15
I need help.

I can run an update through Synaptic Package Manager(GUI) but not on the terminal.

I connect to the internet through a proxy connection to a Windows machine. Under Synaptic, I change the connection through 192.168.0.1:9877.

Works fine through the GUI. But not in the terminal. When I install some downloaded scripts, it needed to download additional software through the terminal. I can't connect to the proxy through the  terminal. 

Need help. How can I connect to the internet through the terminal(with apt-get update)?

I've had the same problem like this before with Bayanihan Linux but solved the problem by specifying the proxy address in the "apt.conf" file. But here in Ubuntu, theres no such file name "apt.conf".

---

### Post by Mr_Grieves on 2006-01-15
Looked here?
```

/etc/apt/apt.conf

```
If there is no file.. perhaps you can create one.

```

whereis apt-get

```
Might get the path to the configuration file.

Or a good old find.

```

find / -name apt.conf

```

---

### Post by kenweill on 2006-01-15
[QUOTE=Mr_Grieves]Looked here?
```

/etc/apt/apt.conf

```[/QUOTE]

There's no such file. Heres the content of /etc/apt directory:

kenweill@server-lazi-cec:/etc/apt$ ls -al
total 32
drwxr-xr-x    3 root root 4096 2006-01-13 06:24 .
drwxr-xr-x  107 root root 4096 2006-01-15 14:18 ..
drwxr-xr-x    2 root root 4096 2006-01-12 02:58 apt.conf.d
-rw-------    1 root root    0 2006-01-12 02:41 secring.gpg
-rw-r--r--    1 root root 1889 2006-01-14 10:56 sources.list
-rw-r--r--    1 root root 1844 2006-01-14 10:56 sources.list.save
-rw-------    1 root root 1200 2006-01-12 02:41 trustdb.gpg
-rw-r--r--    1 root root 2393 2006-01-12 02:41 trusted.gpg
-rw-r--r--    1 root root 2381 2006-01-12 02:41 trusted.gpg~
kenweill@server-lazi-cec:/etc/apt$ cd apt.conf.d/
[email]kenweill@server-lazi-cec:/etc/apt/apt.conf[/email].d$ ls -al
total 28
drwxr-xr-x  2 root root 4096 2006-01-12 02:58 .
drwxr-xr-x  3 root root 4096 2006-01-13 06:24 ..
-rw-r--r--  1 root root   51 2005-09-22 16:12 05aptitude
-rw-r--r--  1 root root  129 2005-03-23 02:19 10periodic
-rw-r--r--  1 root root   85 2005-03-23 08:51 20archive
-rw-r--r--  1 root root  182 2005-09-16 22:42 70debconf
-rw-r--r--  1 root root  116 2005-10-10 19:59 99update-notifier

Its really weird. There's no apt.conf file. Where did it go?

---

### Post by Mr_Grieves on 2006-01-15
AHA!

[https://wiki.ubuntu.com/AptGetHowto?action=show&redirect=AptGetHowTo](https://wiki.ubuntu.com/AptGetHowto?action=show&redirect=AptGetHowTo)

> 
Setting up apt-get to use a http-proxy

gedit ~/.bashrc

add these lines to the bottom of your .bashrc file

http_proxy=http://yourproxyaddress:proxyport
export http_proxy

Save the file. Close your terminal window and then open another terminal window

Test proxy with sudo apt-get update and whatever networking tool you desire. I use firestarter to see active connections.

If you make a mistake and go back to edit the file again, remember to close the terminal and reopen it. It will not function with the new settings until you do. 


---

### Post by kenweill on 2006-01-15
Thanks alot.

Now, I got it working. :smile:

---

### Post by Mr_Grieves on 2006-01-15
Hahaha.. great. I've learned something new aswell :D

---

