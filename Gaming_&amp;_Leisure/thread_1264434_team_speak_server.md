---
title: "team speak server"
date: 2009-09-12
forum: Gaming &amp; Leisure
---

### Post by I WILL DO IT on 2009-09-12
the noobie is back with more questions.

how do i install and run a team speak server??

i look a 3 guides and i get stuck in some places, i thoght it was my comp so i reinstalled unbuntu. i wanna make sher i do it right this time.

plz and thank you

---

### Post by Perfect Storm on 2009-09-12
Teamspeak is in synaptic Package Manager;

```
sudo apt-get install teamspeak-server
teamspeak-server
```

---

### Post by I WILL DO IT on 2009-09-12
cool@cool-desktop:~$ sudo apt-get install teamspeak-server
[sudo] password for cool: 
Sorry, try again.
[sudo] password for cool: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
cool@cool-desktop:~$ sudo apt-get install teamspeak-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  teamspeak-server
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1096kB of archives.
After this operation, 3002kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse teamspeak-server 2.0.24.1+debian-1 [1096kB]
Fetched 1096kB in 13s (80.4kB/s)                                               
Selecting previously deselected package teamspeak-server.
(Reading database ... 121259 files and directories currently installed.)
Unpacking teamspeak-server (from .../teamspeak-server_2.0.24.1+debian-1_i386.deb) ...
Processing triggers for man-db ...
Setting up teamspeak-server (2.0.24.1+debian-1) ...
Adding system user/group teamspeak-server.

cool@cool-desktop:~$ teamspeak-server
Exception EFCreateError in module teamspeak-server.real at 0806F095.
Cannot create file "/usr/lib/teamspeak-server/server.ini". Permission denied.
cool@cool-desktop:~$ sudo teamspeak-server
Error, Either an old instance of teamspeak is still running, or
       an other application is using the tcpquery port!
Error, Server was not started!
cool@cool-desktop:~$

---

### Post by Perfect Storm on 2009-09-12
hold on. I'll see if I can traslate this guide into; ubuntu-ish; [http://www.teamspeak.com/?page=tutorial_b](http://www.teamspeak.com/?page=tutorial_b)

---

### Post by Perfect Storm on 2009-09-12
As the guide suggested that running teamspeak with hosted on another user-account, so I have translated it directly.

first removing the current teamspeak;
```
sudo apt-get remove --purge teamspeak-server
```

Next;
```

sudo su
useradd -d /home/teamspeak teamspeak
cd /home/teamspeak
wget -q http://teamspeak.netfire.com/releases/ts2_server_rc2_202319.tar.bz2
tar -xjf ts2_server_rc2_202319.tar.bz2
cd tss2_rc2
./teamspeak2-server_startscript start
```

---

### Post by I WILL DO IT on 2009-09-12
[SIZE="4"]i guess its safe to say that i need to make a folder?[/SIZE]




cool@cool-desktop:~$ sudo apt-get remove --purge teamspeak-server
[sudo] password for cool: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  teamspeak-server*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 3002kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 122430 files and directories currently installed.)
Removing teamspeak-server ...
Purging configuration files for teamspeak-server ...
dpkg - warning: while removing teamspeak-server, directory `/usr/lib/teamspeak-server' not empty so not removed.
Processing triggers for man-db ...
cool@cool-desktop:~$ sudo su
root@cool-desktop:/home/cool# useradd -d /home/teamspeak teamspeak
root@cool-desktop:/home/cool# cd /home/teamspeak
bash: cd: /home/teamspeak: No such file or directory
root@cool-desktop:/home/cool#


((((FIX)))))




theres a new problem how do i get ip to my teamspeak-server
and config it ect ect

---

### Post by Perfect Storm on 2009-09-12
```
cd /home
ls -a
```


> theres a new problem how do i get ip to my teamspeak-server
and config it ect ect
I don't know. I don't have server(s). I'm only Desktop user. You might ask/search in our server forum.

---

### Post by I WILL DO IT on 2009-09-12
ok, Artificial Intelligence you have been the bigest help ever, what i've been reaching for about a week ect ect you've able to help me complete it in a matter of an hour.


thx your the best

---

### Post by Perfect Storm on 2009-09-12
My pleasure and good luck.

---

