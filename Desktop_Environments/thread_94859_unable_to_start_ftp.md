---
title: "unable to start ftp"
date: 2005-11-25
forum: Desktop Environments
---

### Post by heart_reaver on 2005-11-25
Hello to all 

I wanna start ftp for my local lan so i go to ubuntuguide.org and find ftp section 
and installed. when i rebooted system n try to open [ftp://xxx.xxx.xxx.xxx](ftp://xxx.xxx.xxx.xxx)

where xxx.xxx.xxx.xxx is my ip it shows : conection was refused to connect xxx.xxx.xxx.xxx.

then i try to restart this is what i got

anu@amnesty:~$ sudo /etc/init.d/proftpd restart
Password:
ProFTPd is started from inetd.

---

### Post by oskude on 2005-11-25
try (in the console/terminal)```
ftp anu@localhost
```

edit:
sry, forget that one! (its so wrong) :)

i assume you installed proftpd with "inetd" not "standalone"
thats why you cant start it with "/etc/init.d/proftpd start"
and i dont have a clue about "inetd", try restart :)

or

type```
sudo dpkg-reconfigure proftpd
```select "standalone" and it should start right away, and you can control it with /etc/init.d/proftpd

---

### Post by heart_reaver on 2005-11-26
I have configured it to standalone then this what i m getting

anu@amnesty:~$ ftp anu@localhost
ftp: anu@localhost: Unknown host

---

### Post by oskude on 2005-11-26
[QUOTE=heart_reaver]I have configured it to standalone then this what i m getting

anu@amnesty:~$ ftp anu@localhost
ftp: anu@localhost: Unknown host[/QUOTE]
as i said "sry, forget that one! (its so wrong)" :)

so use any ftp client you want or```
ftp localhost
```and then your user and pass...

---

### Post by heart_reaver on 2005-11-26
no good 

same thing 

anu@amnesty:~$ ftp localhost
ftp: connect: Connection refused
ftp> localhost
?Invalid command
ftp> ftp localhsot
?Invalid command
ftp> ftp
?Invalid command
ftp> exit
anu@amnesty:~$ ftp
ftp>


tell me which file i show you so that u can understand problem batter

---

### Post by oskude on 2005-11-26
do you have a "firewall" in the pc where you installed proftpd? open port 21...

did you try to restart the ftp server ?```
sudo /etc/init.d/proftpd restart
```
do you see "proftpd" in processes ?```
ps aux
```
is there something listening on port 21?```
nmap localhost
```
you may need to install "nmap" for that...

i dont know what to search, proftpd works here out-of-the-box...

---

