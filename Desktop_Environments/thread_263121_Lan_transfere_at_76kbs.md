---
title: "Lan transfere at 76kb/s"
date: 2006-09-22
forum: Desktop Environments
---

### Post by doomstone on 2006-09-22
U'm abit pusseled over why my 2 computers 1 win (server) and 1 linux (desktop) only transfere between them with 76,8 kb/s.
This is a problem becaus i'm trying to back up my server so i can install linux on it (400+ Gb).
Both computers have a 1000 Mbit networke card, and the hub in between is a 10/100/1000 hub. and i know the problem is not on the windows computer.

Any 1 know what the problem might can be?

---

### Post by lamego on 2006-09-22
On the terminal check your network speed setting with:
```
sudo mii-tool
```
What are you using to transfer the files ?

---

### Post by doomstone on 2006-09-23
I have tryed Natilus and a FTP client (and using Filezilla on my win server)

---

### Post by doomstone on 2006-09-23
> doomstone@doomstone:~$ sudo mii-tool
SIOCGMIIPHY on 'eth0' failed: Operation not supported
eth1: negotiated 100baseTx-FD flow-control, link ok
doomstone@doomstone:~$


[IMG]http://www.doomstone.dk/Screenshot.png[/IMG]

---

### Post by Yuzem on 2007-02-10
You must have the same mode for all the devices including the hub.
To set 100MB/s in edgy for eth0:
```
sudo mii-tool eth0 --force=100baseTx-FD
```
In XP go to network connections and right clic the right  connection and select properties, I don't remember the name of the button but is right there on the first tab, settings or properties, to change the device settings. Then on the advance tab look for the option to change to 100 full duplex.
I don't know the hub part...

---

