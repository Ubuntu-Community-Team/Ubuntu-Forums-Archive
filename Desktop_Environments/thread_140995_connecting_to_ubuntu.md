---
title: "connecting to ubuntu"
date: 2006-03-07
forum: Desktop Environments
---

### Post by patelvishaal on 2006-03-07
anyone know a good way of connecting to another ubuntu machine to share files
i have used samba to connect a windows machine to my ubuntu machine, but i wana connect a ubuntu machine to my ubuntu machine

any one have any suggestions, or guides?

its for my computer enginering class in high school :P

---

### Post by taurus on 2006-03-07
Are two machines on the net directly or are they connected through a router?  One way is to install vsftpd or proftpd and ftp stuff back and forth with gftp.  You can also use nautilus to transfer files too.

---

### Post by patelvishaal on 2006-03-08
um i think they r all connected by router, 
i cant use samba to connect the 2 ubuntu machines?

---

### Post by Swiss on 2006-03-08
Samba is for connecting to Windows, not Linux (Ubuntu).

---

### Post by kickaha on 2006-03-08
You are looking for ssh and sshfs (or shfs, in some circles)

ssh is a service that runs on the machine to be accessed, and which allows a 'secure shell' to be established over the net.

sshfs uses ssh services to allow mounting an arbitrary portion of the directory tree on the machine that is running the ssh server under a mount point on your machine.

Setting up ssh is not difficult. If you google for it, you'll find many howtos. The big choice you have to make is whether to run public/private key only, which is a bit more complicated, but a lot more secure. You can also run password access.

You will need to have the touter set up to forward ssh traffic to the machine you want  to access. If you're in a work setting, you're on your own there. :)

You can 'log in' to the remote machine with ssh and it will look just like a local terminal. (I set a profile in my terminal tool so I can tell them apart; different background colour)

You can mount, for example, your home directory on the remote system under your home directory on your local system and copy files back and forth.

google on 'ubuntu shfs' or 'google sshfs' and there's an ubuntu blog article that describes the steps you need to take.

Please note: if your router is on the internet, you will, in short order, be scanned, and hackers from all over will attempt to log in to your ssh server machine. If you're in a work setting, firewalling might help. If you're doing this on your own, you should definitely think of going key-only. They'll scan, but will almost certainly not get in. There are some configuration tweaks, and some tools, that will monitor logs and cut off scanners after some number of failed login attempts, and possibly put them on a blacklist in your /etc/hosts.deny file.

Hope this is what you're looking for.

---

### Post by patelvishaal on 2006-03-08
ok, well we will c
im gona attempt this at school tmr :D, hopefully all goes well

i'm surprised u can't connect using ubuntu to samba that really sucks
today we had a localhost problem with swat.  It was that inetd.conf swat file i had to download

hopefully all goes well

---

### Post by patelvishaal on 2006-03-27
ok, im using swat and samba and i am having problems adding a windows computer

i add the users but i dont know how to connect them to the server, can someone help me and not just give me a link :(

---

