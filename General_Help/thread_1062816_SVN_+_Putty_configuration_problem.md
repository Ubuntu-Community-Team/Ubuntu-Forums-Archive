---
title: "SVN + Putty configuration problem"
date: 2009-02-07
forum: General Help
---

### Post by knight1982 on 2009-02-07
Hi all, this is my first contact with you, I've just arrived.
Well, I am a web developer, I want to switch from Wind to Ubuntu and use it for developing.
My problem is that I am using a SVN repository with a secured tunnel.
In windows, I used SubEclipse with Putty to connect and get Code from the server.
But I found problems to connect using Ubuntu. :(
I did the same configuration like the one on Windows, I installed Subversion, SSh, Putty and SubEclipse.I added the tunnel configuration in the file config under /etc/subversion this way : svn+ssh<port>:<host>/<projectpath>
But I always get this response : Folder '' DOESNT EXIST REMOTELY :(
I hope I'll find a solution to this problem.
Thank you guys for your god work.

---

### Post by bettlebrox on 2009-02-07
I haven't used svn+Eclipse, but on Linux you don't need to use putty, instead use ssh .

---

### Post by knight1982 on 2009-02-07
Thank you for responding.
If this is the case, How to Configure ssh to use the private key and to create a secured tunnel to the server ?

---

### Post by bettlebrox on 2009-02-10
Setting up the secure key isn't too hard, you have to generate the key, then copy the public key to the server you want to connect to. This tutorial looks spot-on:

[http://pkeck.myweb.uga.edu/ssh/](http://pkeck.myweb.uga.edu/ssh/)

Not sure how you configure the tunnel.

---

### Post by bettlebrox on 2009-02-10
The first comment here might help (it's referring to CVS, but it shouldn't be much different for svn):

[http://stackoverflow.com/questions/382353/how-can-i-set-up-eclipse-to-use-ssh-agent-for-cvs](http://stackoverflow.com/questions/382353/how-can-i-set-up-eclipse-to-use-ssh-agent-for-cvs)

---

