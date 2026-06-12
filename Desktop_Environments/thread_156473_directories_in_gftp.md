---
title: "directories in gftp"
date: 2006-04-07
forum: Desktop Environments
---

### Post by GabrielWolff on 2006-04-07
I have a small ftp server, and am using gftp for it.

In one folder I have different files which I would like to move to a different folder on the same server. But I was unable to find out how.

Anyone?

G

---

### Post by dcstar on 2006-04-07
[QUOTE=GabrielWolff]I have a small ftp server, and am using gftp for it.

In one folder I have different files which I would like to move to a different folder on the same server. But I was unable to find out how.

Anyone?

G[/QUOTE]
FTP is a simple protocol for moving files from one system to another, not moving them from one place to another on a remote system.

You will have to copy them to your local system, and then back to the new location on the remote system.

It would probably be easier to make a Telnet - or X - connection to the remote server and do the move with the built-in utilities.

---

### Post by GabrielWolff on 2006-04-07
[QUOTE=dcstar]It would probably be easier to make a Telnet - or X - connection to the remote server and do the move with the built-in utilities.[/QUOTE]


How do I do that. Which program should I use?

G

---

### Post by CrustyDOD on 2006-04-07
Actually you can move folders on the server using FTP client..

Grab folder and move it over the folder you want it in. If you want to move whole folder out of some folder, grab that folder and move it to '..' and release. Folder should be moved then.. Don't know if this works in gFTP but you can try it..

---

### Post by taurus on 2006-04-07
To log into a server, that server needs to have sshd running first.  Then, you can log in like
```

ssh -l userID IP_of_your_server

```
After you enter your password, you can use the mv to move files around and mkdir to create directory.
```

mkdir directory_name
mv filename destination

```
When you are done, just issue bye from the prompt to log out of the server...

---

### Post by GabrielWolff on 2006-04-08
[QUOTE=CrustyDOD]Actually you can move folders on the server using FTP client..

Grab folder and move it over the folder you want it in. If you want to move whole folder out of some folder, grab that folder and move it to '..' and release. Folder should be moved then.. Don't know if this works in gFTP but you can try it..[/QUOTE]

It doesn't work with gftp

Which client would/do you use?

Gabriel

---

### Post by CrustyDOD on 2006-04-08
Ah just tried it, it indeed doesn't work.. I also use gftp but only for file transfers nothing more.. If you have windows, use some ftp client and do it like i said. Filezilla ftp client supports that and probably most of other also.. Also you might want to try some other FTP clients in linux, someone might support this..

---

### Post by taurus on 2006-04-08
I haven't checked it out myself because I don't use it but see if you can do whatever you have in mind with nautilus!!!

---

