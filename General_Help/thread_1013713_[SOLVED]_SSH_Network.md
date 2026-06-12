---
title: "[SOLVED] SSH Network"
date: 2008-12-17
forum: General Help
---

### Post by jake1017 on 2008-12-17
I have two computers with 8.10 installed. I would like to set-up a SSH network between them. Could anyone give me instructions on how to do this?

Thank you

---

### Post by reality1011 on 2008-12-17
you mean you want to connect via ssh from one computer to another?  if so then install an ssh server, a good choice is openssh

---

### Post by jake1017 on 2008-12-17
Yes. Already have SSH installed but went I try to connect I get connection rejected.

---

### Post by Zack McCool on 2008-12-17
Please be more specific on what you are trying to accomplish.  SSH can be used in many ways, so if you tell us what you want to do with it, we'll help you get it done...

---

### Post by jake1017 on 2008-12-17
I go into Places/Connect to Server... and use these settings.

Service Type: SSH
Server: IP of computer I want to connect to.
Port: I leave it blank.
Folder: File directory on the computer I want to connect to.
User Name: I also leave this blank.

When I try to connect I get "Cannot display location: Connection refused by server".

I have also tried.

```
sshfs user@IP:/Directory /Mount/Directory

```

But get the error read: Connection reset by peer.

---

### Post by vanadium on 2008-12-17
see [http://www.howtogeek.com/howto/ubuntu/how-to-mount-a-remote-folder-using-ssh-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/how-to-mount-a-remote-folder-using-ssh-on-ubuntu/)

---

### Post by Zack McCool on 2008-12-20
Have you installed the ssh server on the target computer?  

```
 sudo apt-get install openssh-server 
```

By default, the server is not installed...

---

