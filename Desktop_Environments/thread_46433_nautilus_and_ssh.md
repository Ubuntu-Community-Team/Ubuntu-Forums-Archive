---
title: "nautilus and ssh"
date: 2005-07-04
forum: Desktop Environments
---

### Post by python_guy on 2005-07-04
I can access my other using ssh command line.

However, I cannot do it with hoary's nautilus?
nautilus:file| connect to server
type: ssh
server: david@192.168.1.1

or type: ssh
server: 192.168.1.1
username: david

it just trying to connect and nothing happen, did I do anything wrong? do I need to fetch additional packages?

---

### Post by X3N on 2005-07-04
In "server" you only need the hostname or IP, not username@hostname or ip 
also
- Make sure you have "ssh" installed
- Make sure the computer you're trying to connect to has the ssh server runing 
- Make sure the computer you're trying to connect to has ssh configured to allow sftp (should be on by default)

---

### Post by crashtest on 2005-07-04
The first time I connect to a new machine with SSH, I do it in a terminal, because you will get that initial dialog about  about accepting the "key" for the remote machine.  Something like: 
The authenticity of host 'ssh-server.example.com (12.18.429.21)' can't be established.   RSA key fingerprint is 98:2e:d7:e0:de:9f:ac:67:28:c2:42:2d:37:16:58:4d.   Are you sure you want to continue connecting (yes/no

I'm not sure if this pops up when you make your initial connection using a gui?

After this initial connection, I just use gftp.

---

### Post by python_guy on 2005-07-05
x3n, watch my post again and you can see that I tried

crashtest, the commandline is working perfectly. It is just that nautilus doesn't work. I also tried sftp://user@ip_of_another_pc:22/

thanks anyway

---

