---
title: "[SOLVED] How do I setup an FTP Server?"
date: 2009-01-07
forum: General Help
---

### Post by studentidiot on 2009-01-07
Is there an easy way to setup an ftp server with authentication in Ubuntu 8.10.

I've tried guides online but either they don't work or I'm doing it wrong.(Probably the latter.)

THANKS!

---

### Post by albinootje on 2009-01-07
> **studentidiot said:**
> Is there an easy way to setup an ftp server with authentication in Ubuntu 8.10. 

Did you try this howto :
[https://help.ubuntu.com/community/PureFTP](https://help.ubuntu.com/community/PureFTP)

Here's a page with some links to other admin GUI for PureFTP :
[http://www.debianhelp.co.uk/pureftpweb.htm](http://www.debianhelp.co.uk/pureftpweb.htm)

---

### Post by studentidiot on 2009-01-08
Is there something like Filezilla for Ubuntu?

---

### Post by Peter09 on 2009-01-08
If this is for personal use then scp is easier and better. Install openshh-server.

---

### Post by sendblink23 on 2009-01-08
> **studentidiot said:**
> Is there something like Filezilla for Ubuntu?

Yes there is FileZilla on  Linux


just google it:  filezilla on linux

:P  **its open source***

---

### Post by studentidiot on 2009-01-08
I mean Filezilla server.

I need something for personal use. I need to share files beteeen Ubuntu and Mac machines.

I was using Filezilla Server on Windows to serve to my Linux and Mac computers, but I had it committed to a mental institution.

Samba can't play nice with Mac on either Windows or Ubuntu. Pluse turning on windows sharing dramatically slows down my Ubuntu machines for some reason.

---

### Post by Peter09 on 2009-01-08
Do try ssh - its a secure inter machine protocol, its in the repositories. It allows remote desktops, remote file shares etc.

---

### Post by studentidiot on 2009-01-08
> **Peter09 said:**
> Do try ssh - its a secure inter machine protocol, its in the repositories. It allows remote desktops, remote file shares etc.

Thanks!

Might be a little over my head but I'll give a go.

---

### Post by Peter09 on 2009-01-08
It is easier to setup than FTP. Which way are you wanting to transfer files?

---

### Post by studentidiot on 2009-01-08
From 4 or 5 macs and ubuntu laptps to one desktop.

And all to be able to retrieve, delete, and rename the files the others put on there.

mostly large movies if that matters

---

### Post by Peter09 on 2009-01-08
OK, well on the desktop do

```
sudo apt-get install openssh-server
```

thats it for the desktop.

To test on the desktop try

```
ssh -X <username>@localhost xterm
```

This should give you an xterminal.

Further you can try right click on the top panel and add an applet (Connect to Server). Once added use it to select SSH and server=localhost. This should give you scp.

For security its best to edit your ssh config.

```
gksudo gedit /etc/ssh/sshd_config 
```

and make sure the line with 
PermitRootLogin 
is set to no

PermitRootLogin no

just restart ssh
```
sudo /etc/init.d/sshd restart
```

and the servers all done.

---

### Post by studentidiot on 2009-01-08
0_o

I think I'm going to have to reinstall windows again.

Thanks though!!!

---

### Post by albinootje on 2009-01-08
> **studentidiot said:**
> 
I think I'm going to have to reinstall windows again.


Why ?!
Here's a scp/sftp client for MacOSX : [http://cyberduck.ch/](http://cyberduck.ch/)

---

### Post by morningboat on 2009-01-08
> **studentidiot said:**
> 0_o

I think I'm going to have to reinstall windows again.

Thanks though!!!

You don't need to reinstall windows to get that. You can have a look at the CrossFTP Server ( [http://www.crossftp.com/crossftpserver.htm](http://www.crossftp.com/crossftpserver.htm) ), a GUI FTP server which works similar to the FileZilla server. There are some tutorials on that web site as well.

---

### Post by studentidiot on 2009-01-08
Thank you! CrossFTP it is.

---

