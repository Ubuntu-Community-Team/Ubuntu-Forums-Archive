---
title: "file copy from one Ubuntu to another"
date: 2006-08-20
forum: Desktop Environments
---

### Post by justinj100 on 2006-08-20
Hi all,

I have just upgraded my machine to a amd64 X2 and installed the 64 bit version of 6.06. I have the 'old' machine with thr 32bit version installed both on the same home network (192.168.0.1-255). However, neither will see the other! They will ping each other but will not connect.

I have installed apache on the 32bit version. if I open a browser on it, type in the machines own IP, I see the files on that machine. if I try it on the 64 bit machine (ip address of the 32 bit machine) I get a time out. I have even installed openssh on the 32 bit machine and no connection with ssh from the command line either.

I have even installed webmin on the 32bit machine, but any other machine (windows laptop of the 64bit ubuntu) will not see either ubuntu machine on the network!

I have tried activating file sharing too but to no avail.

I have tried for many hours now and having to result to expert help (i hope!) Any help would be greatly appriciated.

Thanks in advance,

Justin

---

### Post by steve.horsley on 2006-08-20
On one machine, install package **openssh-server**. Given that you can ping one machine from the other, you should be able to use ssh.

A thought on apache - it doesn't get installed listening only on the lopback address of 127.0.0.1 does it?

---

### Post by justinj100 on 2006-08-20
Hi, thanks for the post. However, I have tried installing SSH server to no avail, same problem.

Apachse is installed, not sure about the loop back, where can I check?

JJ

---

### Post by ardchoille on 2006-08-20
> **steve.horsley said:**
> On one machine, install package **openssh-server**. Given that you can ping one machine from the other, you should be able to use ssh.

A thought on apache - it doesn't get installed listening only on the lopback address of 127.0.0.1 does it?

No, apache is install with this in the /etc/apache2/apache2.conf file:

```

Listen 80

```

If you want apache to only listen for requests from 127.0.0.1, then you need to change that to this:

```

Listen 127.0.0.1:80

```

That's what I did to keep apache from listening for requests from the internet. Mode info can be found at: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by justinj100 on 2006-08-21
but effectivley, that is what I want it to do right? listen to requests from other machines. It will not listen to requests from the Internet as it is behind a NAT firewall....

---

### Post by steve.horsley on 2006-08-21
So why can't you connect using SSH? You should be able to.

What happens when you log onto the machine that's not running the ssh server, and try and ping the ssh server machine (e.g. ping 1.2.3.4)? 
What happens when you try and connect to it using ssh (e.g. ssh 1.2.3.4)?

On the machine running the ssh server, check it's listening with this command:
ifconfig -lnt

Post the results here and we'll try to make sense of them.

---

