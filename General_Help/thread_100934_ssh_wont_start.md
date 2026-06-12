---
title: "ssh wont start"
date: 2005-12-08
forum: General Help
---

### Post by korkow on 2005-12-08
Hey, Im having trouble with getting ssh to start. When I type "/etc/init.d/ssh start", I get this...

 * Starting OpenBSD Secure Shell server...                                      
host key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_dsa_key
Disabling protocol version 2. Could not load host key
sshd: no hostkeys available -- exiting.
                                                                                                                          

Korkow

---

### Post by mlomker on 2005-12-08
I haven't set it up myself, but some Google searches suggested that either there is a permission problem in reading your keys or you didn't generate the keys.  You are using **sudo** when you try to start it?

I [found this]("http://www.dbforums.com/showpost.php?p=4093218&postcount=2") but it isn't specifically Ubuntu.

---

### Post by korkow on 2005-12-08
yes, I am using sudo, and iv'e tried doing it as root. The link you gave me dosn't help because I don't seem to have a /etc/rc.network

---

### Post by madtinkerer on 2005-12-09
It looks as though the keys haven't been created yet.  Have you tried ssh-keygen yet?  That should generate a key pair and solve that problem.

---

### Post by mlomker on 2005-12-09
[QUOTE=korkow]yes, I am using sudo, and iv'e tried doing it as root. The link you gave me dosn't help because I don't seem to have a /etc/rc.network[/QUOTE]

The ssh-keygen command was the relevant part of that post.

---

### Post by korkow on 2005-12-09
err.. I have no idea what to do still..

---

### Post by madtinkerer on 2005-12-09
you need to run the command ssh-keygen.   Open a terminal and type ssh-keygen and hit enter.  It will create the keys that the error you had complained were missing.  Once you do that, try to start ssh again.

---

### Post by korkow on 2005-12-09
erm, when I run i run ssh-keygen. I get "must specify a key type [-t], usage ssh-keygen [options].

---

### Post by madtinkerer on 2005-12-09
try ssh-keygen -t dsa.  If you run into problems like this again, you can type "man programname)"  it will tell you how to use the program.  good luck

---

### Post by damp on 2005-12-09
try this

```
damp@defiant:/etc$ sudo ssh-keygen -t rsa
Password:
Generating public/private rsa key pair.
Enter file in which to save the key (/root/.ssh/id_rsa):
Created directory '/root/.ssh'.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /root/.ssh/id_rsa.
Your public key has been saved in /root/.ssh/id_rsa.pub.
The key fingerprint is:
a1:42:b5:cb:26:73:6d:35:3e:91:7d:09:1a:db:14:eb root@defiant
damp@defiant:/etc$

```

---

### Post by korkow on 2005-12-09
This is really weird, nothing is working. I tried doing just what you said, and I also tried putting it in /etc/ssh/ssh_host_rsa_key. (also in dsa). Im getting no errors during keygen, but ssh is still being crappy.

---

### Post by Granduke on 2005-12-09
Don't know if this is the problem you are having.  I got was getting the same message you were getting.  Then I did this:

granduke@ubuntu:~$ sudo /etc/init.d/ssh start
 * Starting OpenBSD Secure Shell server...                               [fail]
granduke@ubuntu:~$ sudo /etc/init.d/ssh restart
 * Restarting OpenBSD Secure Shell server...                             [ ok ]
karl@ubuntu:~$ sudo /etc/init.d/ssh stop
 * Stopping OpenBSD Secure Shell server...                               [ ok ]
granduke@ubuntu:~$ sudo /etc/init.d/ssh start
 * Starting OpenBSD Secure Shell server...                               [ ok ]

And it seems to work now.

---

### Post by damp on 2005-12-10
Whoops... I should have tested things on my box before replying (just got Ubuntu on my laptop today)...

When you generate those keys (RSA is better from what I gather, but having RSA and DSA keys won't hurt), they'll be placed into /root/.ssh/id_rsa by default (and id_rsa.pub...same with the DSA keys).

The .pub files are your public keys, which you can give to other machines that want to connect securely to your box via [public-key encryption]("http://en.wikipedia.org/wiki/Public-key_encryption").  The id_?sa files (where the "?" stands for either "r" or "d") are your SECRET keys.  Don't give those out!!!

When running ssh-keygen, save the files as /etc/ssh/ssh_?sa_host_key (and ssh_?sa_host_key.pub, respectively)

Then, make sure any instances of sshd are stopped:

```
root@defiant:~# ps auxww | grep ssh
root      8194  0.0  0.2   3544  1532 ?        Ss   00:41   0:00 /usr/sbin/sshd
root      8494  0.0  0.0   1624   488 pts/1    R+   00:52   0:00 grep ssh
root@defiant:~# kill -9 8194

```

Now, it's time to start sshd.

```
sudo /etc/init.d/ssh start
 * Starting OpenBSD Secure Shell server...                               [ ok ]
```

Hope that helps.  Sorry for the super delayed reply!

_damp

---

### Post by mlomker on 2005-12-10
korkow, is it the openssh-server package that you installed or something else?  I'm curious because I just installed it to walk through the steps and it automatically generated the keys during the install:

```

mlomker@mlomkernote:/etc/init.d$ sudo apt-get install openssh-server
Password:
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  ssh-askpass rssh
The following NEW packages will be installed:
  openssh-server
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/195kB of archives.
After unpacking 524kB of additional disk space will be used.

Preconfiguring packages ...
Selecting previously deselected package openssh-server.
(Reading database ... 105867 files and directories currently installed.)
Unpacking openssh-server (from .../openssh-server_1%3a4.1p1-7ubuntu4_i386.deb) ...
Setting up openssh-server (4.1p1-7ubuntu4) ...
Creating SSH2 RSA key; this may take some time ...
Creating SSH2 DSA key; this may take some time ...
 * Restarting OpenBSD Secure Shell server...                             [ ok ]

```

The keys were placed in this directory:

```

mlomker@mlomkernote:/etc/ssh$ ls -l
total 156
-rw-r--r--  1 root root 132839 2005-10-10 15:10 moduli
-rw-r--r--  1 root root   1361 2005-10-10 15:10 ssh_config
-rw-r--r--  1 root root   1889 2005-12-10 09:22 sshd_config
-rw-------  1 root root    668 2005-12-10 09:22 ssh_host_dsa_key
-rw-r--r--  1 root root    606 2005-12-10 09:22 ssh_host_dsa_key.pub
-rw-------  1 root root    887 2005-12-10 09:22 ssh_host_rsa_key
-rw-r--r--  1 root root    226 2005-12-10 09:22 ssh_host_rsa_key.pub

```

I wonder if running **sudo dpkg-reconfigure openssh-server** would have taken care of it as well?

---

### Post by korkow on 2005-12-10
Hm... reinstalling it seemed to work! I definietly  had it installed beforehand, but I guess there was something wrong with the install. (I did it with "sudo apt-get install" the first time, which is strange that something went wrong. Anyways, ssh is back in buisness! Thanks

---

### Post by hoodwink on 2005-12-10
The big question is: why wasn't this done automatically at install time? It certainly was for my hoary -> breezy setup. I've never had to tinker with ssh; it just works.

---

### Post by damp on 2005-12-10
I snagged it via Synaptic.  For some reason, the hostkeys weren't installed by default, so it was the same problem for me.  Maybe a minor bug in the package?  :-k

---

### Post by CA1900 on 2006-03-03
Well, I ran into this too.  Fresh install of Ubuntu 5.10 as of yesterday evening.  (My first foray into linux!)   Did the **sudo apt-get install openssh-server**.  Everything seemed to install fine, but it wouldn't run -- I got the same errors regarding the host keys.   I removed and reinstalled it with apt-get.  Same problem.  I repeatedly tried rebuilding the keys.  That process was sucessful, but the server still wouldn't read them.

I tried mlomker's idea of using **sudo dpkg-reconfigure openssh-server**, and it gave me this response:
   /usr/sbin/dpkg-reconfigure: openssh-server is broken or not fully installed

Great...   However, on a whim, I decided to try one more thing -- removing the server, and deleting the keys entirely before reinstalling:
[html]
sudo apt-get remove openssh-server
sudo rm /etc/ssh/ssh_host_*
sudo apt-get install openssh-server
[/html]

This time, it worked.  The SSH is up and running.  I'm not sure why it wouldn't read the keys even after they were rebuilt, but killing *everything* and reinstalling seemed to do the trick.  Hope that helps the next guy in my shoes.  :D

---

### Post by Rizado on 2006-03-03
Easiest way to fix it is to run "sudo ssh-keygen -t dsa -f /etc/ssh/ssh_host_dsa_key" and "sudo ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key" and then change the permissions to not be readable by anyone except root.

---

