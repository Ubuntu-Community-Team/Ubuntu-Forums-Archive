---
title: "Need help SSH / gFTP transfers"
date: 2005-12-12
forum: General Help
---

### Post by bananaman on 2005-12-12
Im sorry, im a complete noob and i dont know what the hell im doing...

Ive been trying to share files between 2 ubuntu desktops using a crossover cable for the last 4 hours and i am really frustrated now...i just read tid bits of information on ssh and using gftp to do it... but cant figure out how all those little bits of info come toghether... ive gone through samba, nfs and now im with gftp which id like to stick with...

ive been generating keys, ive been installing packages...the truth is i dont know what im doing and i need help please...

so please, please...tell me how i can connect from one computer to the other using gftp... ive pinged successfully between them... but when i try to connect using ftp it asks me for a user name and password which i obviously dont know because i havent created...

please help me i beg you...
ps. too bad theres not a smiley representing a frustrated suicidal expression, this will have to do... :confused:

oh and uh... a step by step wouldnt hurt...
thank you very much in advance...

---

### Post by ggozad on 2005-12-12
Hi,
I am not gonna tell you how to do it with ftp since you need to setup an ftp server... Through scp it is really easy though (scp is a program that copies using encryption). 
So assuming you want to copy to a machine with IP 192.168.0.2 you will do

```
scp filename user@192.168.0.2:
```

where user is the username at that machine. This will copy it to the home directory.

If you want to copy recursively (entire directories and the directory tree under them) you would do
```
scp -r directory user@192.168.0.2:
```

---

### Post by rapidwiz on 2006-12-09
I use gFTP to copy Images from a linux server to another, just type your servername or ip at the top, port 22, and use SSH2 as the protocol, as long as you have a sftp server setup correctly, works like a dream.

You can also check Options and make sure your SSH Prog is "ssh", leave SSH prog params blank.

I also copy 1GB files across with no issues.

---

