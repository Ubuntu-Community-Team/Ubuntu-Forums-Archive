---
title: "Filesharing service advice?"
date: 2008-12-26
forum: General Help
---

### Post by torp74 on 2008-12-26
Hello all,

Santa brought me a new 1tb external drive, and I want to fill it with files >4gb and share them with my kids located on opposite coasts. My broadband is roadrunner 5 mbps, and I am running ubuntu 8.10. This server needs to;

- Simple so that I can manage it (newbie to running servers)
- Cross platform friendly (one kid runs an apple, the other vista)
- Secure (I am behind the roadrunner, and a local firewall)
- Run in the background (running 24/7)

I have installed both vsftpd, and pure-ftpd, and have no idea how to proceed. Any assistance or guidance would be most helpful. I am open to any and all ideas.

Regards,

torp74

---

### Post by albinootje on 2008-12-26
> **torp74 said:**
> 
I have installed both vsftpd, and pure-ftpd, and have no idea how to proceed. 

First of all, you can, by default only run one kind of ftp-server at the same time.
If you really would want two different ftp-servers running, you would need to change the default port 21 in the config to something else which is not in use.

Do you want your kids to fetch the data, or do you want them to be able to upload data too ?
If you only want them to download data, I suggest to install a web-server instead, for these two reasons :

1) Setting up a firewall for http (web) is so much easier than for ftp
2) In general a ftp-server is harder than a web-server to make it more secure for 24/7 access.

---

### Post by torp74 on 2008-12-26
> **albinootje said:**
> First of all, you can, by default only run one kind of ftp-server at the same time.
If you really would want two different ftp-servers running, you would need to change the default port 21 in the config to something else which is not in use.

Do you want your kids to fetch the data, or do you want them to be able to upload data too ?
If you only want them to download data, I suggest to install a web-server instead, for these two reasons :

1) Setting up a firewall for http (web) is so much easier than for ftp
2) In general a ftp-server is harder than a web-server to make it more secure for 24/7 access.

Hopefully the users would be able to upload files into the system, so I was thinking ftp server. I will certainly only run one server, I just don't know what service to go with.

Regards,

torp74

---

### Post by albinootje on 2008-12-26
> **torp74 said:**
> Hopefully the users would be able to upload files into the system, so I was thinking ftp server. I will certainly only run one server, I just don't know what service to go with.


The safest is to offer your kids scp/sftp access, then they can use nice GUI-apps like cyberduck for MacOSX, and winscp for Windows to download and upload.

You could give them scponly shells instead of a normal user-account, to make it even safer.

One other drawback of the default ftp-servers installations is that password go over the internet as plain-text and could be sniffed by others and abused. That's no issue with ssh/scp/sftp.

Ssh and scponly are even much easier to setup, I'm using vsftpd on a local file-server, and I can tell you that you will have to edit that vsftpd config file, and that's not very easy.
With ssh you basically do the following :
1) install openssh-server and scponly with : 
```

sudo apt-get install ssh scponly

```
2) create the user accounts for the kids, and make their shell not bash but scponly (use strong passwords!)
3) do the port_forwarding for ssh 
  (and perhaps you want to change and run ssh on a non-default port)
4) make some symbolic link in their home directories pointing to the download directory
5) set proper permission on the download/upload directory

That's all.
The only advantage I see with FTP compared to ssh, is that FTP is faster.

But try it out, and see how it goes, and report back.

---

