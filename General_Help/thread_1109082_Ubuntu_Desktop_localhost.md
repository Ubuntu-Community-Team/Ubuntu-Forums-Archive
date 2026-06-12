---
title: "Ubuntu Desktop localhost"
date: 2009-03-28
forum: General Help
---

### Post by wongpk on 2009-03-28
I don't know how it calls, but I would like to know how can I make ubuntu (Desktop version) to work like localhost/server? With Apache, PHP and etc, is there anyway to do it, or it has it already installed?

---

### Post by cosine352 on 2009-03-28
you can do ssh

> sudo apt-get install openssh-server
ssh localhost
exit

This will set up a ssh server in the desktop. 
Now from a remote computer or a computer in network 
>  ssh -X user_desktop@ipaddress
'user_desktop' is the user of the desktop you want to connent to and the 'ipaddress' is the ip address of the desktop you want to connect to. 
This way you will get a command promt to do your stuf remotely. you can also use GUI as here we have used 'ssh -X'. 

To transfer files I use
> nautilus sftp://user_desktop@ipaddress 

Hope this helps.

---

### Post by wongpk on 2009-03-28
But it shows me this message:

wong@wongpk:~$ sudo apt-get install openssh-server
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
wong@wongpk:~$ 

how come? This also happen when I wanna install vista font,,,

---

### Post by cosine352 on 2009-03-28
> **wongpk said:**
> But it shows me this message:

wong@wongpk:~$ sudo apt-get install openssh-server
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
wong@wongpk:~$ 

how come? This also happen when I wanna install vista font,,,

post the output of this command in the terminal

> ps -e | grep -e apt -e adept | grep -v grep

---

### Post by wongpk on 2009-03-28
Then it comes this message:

grep: adept: No such file or directory

Or I should install something else?

---

### Post by cosine352 on 2009-03-28
make sure no other package mannager is running (like 'synaptic') and then try

if you're sure that no apt/adept/dpkg processes are running:

> sudo rm /var/lib/dpkg/lock
If that does not work, try
> sudo killall apt-get
sudo killall aptitude


---

### Post by wongpk on 2009-03-28
Not exactly what I'm looking for. But it's fine, I guess I would just go online and test online instead. Because previously when I'm using Windows, I would install Apache etc to test my web locally. But I don't know how to do it in Ubuntu. Well, test online will do though...

---

### Post by cosine352 on 2009-03-28
have a look at this

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by wongpk on 2009-03-29
Great. Thanks! This is long, gonna take my time understand them :)

---

