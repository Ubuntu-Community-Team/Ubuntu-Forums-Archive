---
title: "need help setting up a file server"
date: 2006-08-01
forum: Desktop Environments
---

### Post by clint1010 on 2006-08-01
Hi all

I am relativley new to Linux and Ubuntu outside of a desktop environment, and require assistance in setting up a file server. My requirements are;

1)Server runs Ubuntu and machines that will be connecting to this server run windows. They are outside my LAN and will need to connect via the WWW.

2)The server will store documents that are required for use by client machines. Documents will be opened and edited by the remote machines and need to be saved back to the original location on the server. If a document is opened by one machine, other machines must not be able to access it untill the document is saved and closed.

3)I still require a desktop environment on the server as i currently run other services on it.

I need advice on what software to run for the server, and what client software to run on the windows and potential ubuntu clients

A how-to on this procedure would be great if anyone can point me in the right direction.

Thanks

---

### Post by frodon on 2006-08-01
re-opened at user request.

BTW clint1010, i wrote an guide about setting a ftp server with ubuntu, it may help you :
[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

---

### Post by nihilocrat on 2006-08-01
You will probably want to go one of two ways, FTP or Samba. Look them up in the Wiki, it should have some decent HOWTOs.

FTP will require FTP clients on your client boxes and thus would possibly be a little annoying. Samba wouldn't require anything at all from the clients and would provide filesharing with the exact same interface you see in Windows filesharing. I'm not familiar with ways of securing Samba properly for internet use, though, as I only have experience setting it up in intranets.

File-locking might not be available at the server level in either of these methods. I know that if I try to access a document someone has open with MS Office, it will only let me open it read-only. I'm not sure if this is a SMB-specific thing or an Office-specific thing.

---

### Post by clint1010 on 2006-08-01
Thanks for the tips guys, much appreciated.

Frodon, will proftpd provide the functionality i require?

thanks again
Clint

---

