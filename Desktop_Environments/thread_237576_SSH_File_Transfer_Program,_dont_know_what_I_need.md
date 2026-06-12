---
title: "SSH File Transfer Program, dont know what I need"
date: 2006-08-16
forum: Desktop Environments
---

### Post by cobbweb on 2006-08-16
hi, 

  For class I have to SSH programs into our linux labs, but right have been just copy and pasting. Is there a program that I can just save my .cpp file and send it somehow over the SSH server to my linux labs?? Also what would the sudo apt-get install command be for that program and/or what would be the terminal command to just do that? Thanks 

 Cobbweb

---

### Post by DoctorMO on 2006-08-16
In the terminal (man ssh):

scp localfile.cpp [email]username@remote.host.com[/email]:/remote/folder

In Gnome:

Places > Connect to Server

Service Type: SSH, all the other information is self explanitory.

---

### Post by ardchoille on 2006-08-16
> **cobbweb said:**
> hi, 

  For class I have to SSH programs into our linux labs, but right have been just copy and pasting. Is there a program that I can just save my .cpp file and send it somehow over the SSH server to my linux labs?? Also what would the sudo apt-get install command be for that program and/or what would be the terminal command to just do that? Thanks 

 Cobbweb

I copy files via ssh a lot, there should be a copy of scp on your Ubuntu box.

usage:
To copy a file from a remote machine to your machine via ssh:
```

scp user@host:/path/file /path

```


To copy a file from your machine to a remote machine:
```

scp /path/file user@host:/path

```

---

