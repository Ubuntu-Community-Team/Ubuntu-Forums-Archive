---
title: "Trouble mapping drives"
date: 2007-11-03
forum: Desktop Environments
---

### Post by kip1479 on 2007-11-03
Hey guys,

 Brand new to Ubuntu/Linux. Yay! Im trying to map to ubuntu from my XP Pro box. Not sure if its even possible. I want to move all my media fiels over the the linux box as Im playing around setting up a media center type machine. I dont see the computer when I browse and mapping to IP address also does not work.

 Am i just heading in the totally wrong direction and not doing it right or attempting some thing that wont work. 

Any help would be appreciated. Thanks.

---

### Post by SpongeTheHumble on 2007-11-03
It is possible to move those multimedia files from your xp box.

I assume your xp box is in your local network? What error message does it give you when you try to connect via IP address? No challenge screen?

The XP box has to be set to recieve connections ragarding login info.

sorry, i can't help more im just starting my transition. gl

---

### Post by Prospero2006 on 2007-11-03
File Sharing:

First, on the linux machine:
```


sudo apt-get install samba


```
Let's assume the following:
Linux IP: 192.168.1.10
Win IP: 192.168.1.20

On the linux machine open up /etc/samba/smb.conf

Create an entry like this:

```


[downloads]
   comment = downloads
   path = /downloads
   guest ok = no
   browseable = yes
   create mask = 0777
   directory mask = 0777

```
This little chunk assumes I have a directory called /downloads

Do an smbd restart

Go to the windows machine:
Right Click on My Computer
Choose 'Map Network Drive'
Type:
\\192.168.12.10\downloads

It should prompt you for a username and password, which you'll need to set
up on the linux box with

```


smbpasswd -a username

```
I hope that helps
Pros
__________________

---

### Post by kip1479 on 2007-11-04
Pros,
 Thank you very much. That worked beautifully. 
 
 Def going to take some getting used to but this software is great, i like being able to control most if not all of the aspects of the software and apps that i install with out all the MS crap. Thanks again.

---

