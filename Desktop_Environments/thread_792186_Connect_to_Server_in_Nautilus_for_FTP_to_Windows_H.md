---
title: "Connect to Server in Nautilus for FTP to Windows Host broken"
date: 2008-05-12
forum: Desktop Environments
---

### Post by emitchlpd on 2008-05-12
When I use the Connect to Server tool (Nautilus) to create an FTP connection to a Windows FTP server, I can connect, but none of the contents of the remote server are shown.

I've seen a few threads about this, but none with answers that work for me. This worked under 7.10, but now under 8.04 it's not working.

It would be great to have this working because I have a few remote servers that I need to connect to with FTP.

---

### Post by radiobrain on 2008-05-17
Hello There,

I have the same problem with my FreeBSD server. I cannot connect to them with Hardy.

Nautilus tell me in french :
Désolé, impossible d'afficher tout le contenu de «*/ sur [www.myhost.ch*»*:](www.myhost.ch*»*:) Impossible de se connecter à l'hôte

Traduction:
Sorry, impossible to show all the content of  / on [www.myhost.ch:](www.myhost.ch:) Impossible to connect to host


I can connect via ftp in cli, via ftp with firefox but not with Nautilus and Nautilus is very more user friendly than the others.

I'm going to research about this prob, but if you have a answer, it will be good.

Thx for reading.

---

### Post by lavinog on 2009-03-16
I am having the same problem with a clients ftp server
```
220 Web47 Microsoft FTP Service (Version 5.0).
```
I can connect with all sorts of ftp clients except nautilus.
Nautilus connects, but fails to display any contents. No errors or anything.
The root folder contains:
```

03-20-01  02:21PM       <DIR>          database
06-14-07  05:42AM       <DIR>          html

```

Is there a way to get nautilus to display a connection log?

---

### Post by MacKai on 2009-03-30
same here... anyone find an answer?

---

### Post by ArtInvent on 2009-04-03
BUMP. 

Same thing here. All of these tools work just fine for other FTP sites. But I have one that says it's a Windows NT ftp server. I can connect to it in FileZilla just fine. I can connect from another XP machine, from a Vista machine, and from an XP virtual machine on the Ubuntu host. But from Nautilus, Konqueror, Dolphin - nothing. It seems to log on but then there are no files or directories visible. Also nil using the Firefox plugin FireFTP.

Also, if I log in with the command line ftp I can ls and see the contents etc. just fine. But not with these file browsers. What gives?

---

### Post by legion1978 on 2010-12-06
BUMP?
really, 2 years later still some unresolved issue on this...
The problem is with the root path. it does shows the files for a second, then dissapear. In subfolders, this does not occur.
Any ideas?

---

### Post by legion1978 on 2010-12-27
ALright.. turns out the files *are* listed, but nautilus defaults root to / whereas on these windows servers should be /username/ so, pressing ctrl+L and putting it in, shows the root files :)

Still timeouts a lot tho ¬¬

---

