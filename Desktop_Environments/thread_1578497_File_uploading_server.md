---
title: "File uploading server"
date: 2010-09-20
forum: Desktop Environments
---

### Post by PHANTOM X on 2010-09-20
What would be the best server be to allow uploading files from anyone anywhere? I'm thinking on installing a Samba File Server for this, but I'm sure on the best way to setup? I don't plan on doing a static IP at this time as it costs extra from our isp and they said they don't change often.

---

### Post by cj.surrusco on 2010-09-20
I would recommend using the SSH transfer protocol, SFTP. It is slightly harder to configure and use, but more more secure than FTP. The advantage of FTP is that it can be accessed by almost any web browser or most file browsers.   

SFTP is supported by default in Ubuntu, and there is a program called WinSCP that you can use for Windows.

---

### Post by endotherm on 2010-09-20
samba is a network protocol, whereas you need a web-capable protocol, like sftp/scp or even good old http.

---

### Post by PHANTOM X on 2010-09-20
> **cj.surrusco said:**
> I would recommend using the SSH transfer protocol, SFTP. It is slightly harder to configure and use, but more more secure than FTP. The advantage of FTP is that it can be accessed by almost any web browser or most file browsers.   

SFTP is supported by default in Ubuntu, and there is a program called WinSCP that you can use for Windows.


Cool. How do I set that up?

---

### Post by PHANTOM X on 2010-09-20
> **endotherm said:**
> samba is a network protocol, whereas you need a web-capable protocol, like sftp/scp or even good old http.

I see.

---

### Post by cj.surrusco on 2010-09-20
> **PHANTOM X said:**
> Cool. How do I set that up?
Just install openssh-server on the computer that you want to upload the files to and you will be able to access it from other computers.

---

### Post by PHANTOM X on 2010-09-20
> **cj.surrusco said:**
> Just install openssh-server on the computer that you want to upload the files to and you will be able to access it from other computers.


Thanks.:)

---

### Post by PHANTOM X on 2010-09-21
I have some concerns on connecting to the server. I installed the openssh-server, but I'm lost on how to connect to it. Do I connect by ip, ftp program or something else?

---

### Post by LinuxPhreak on 2010-09-21
What I would recommend is vsftpd. That is what I have on my server.

```
sudo apt-get install vsftpd
```

or 
[Install VSFTPD Here]("apt://vsftpd")

After it is installed you will need to modify the configuration files of vsftpd
located in /etc/vsftpd.conf the file is pretty self a explanitory.

Once you have your very secure FTP server set up you may want to use an FTP 
on the computers your uploading content from. I would recomemd Filezilla. If 
I remember correctly they have versions of Filezilla for Windows, Mac OSX and Linux.
Filezilla is in most Linux repos including Ubuntu. 

Alternative FTP Servers are ProFTP which also has nice GUI front end called GADMIN. This is nice if you
if you prefer guis.

---

### Post by PHANTOM X on 2010-09-21
That worked great thanks. But I'm finding that anyone can just login and destroy folders and settings. Anyway to restrict them to one folder?

---

### Post by cj.surrusco on 2010-09-22
Yes, you would want to chroot them. 
So, add this to your vsftpd.conf:

chroot_local_user=YES

That will restrict them to their home directory.

---

### Post by LinuxPhreak on 2010-09-23
> **PHANTOM X said:**
> That worked great thanks. But I'm finding that anyone can just login and destroy folders and settings. Anyway to restrict them to one folder?

Their where several different suggestions that where thrown at you. Please state what suggestion you chose that worked great for you? If you installed VSFTPD then you need to configure the configuration file to restrict users from doing certain things. If you copy and paste your config file we will be able to tell you what is wrong.

---

### Post by mister_p_1998 on 2010-09-23
If you want an easy no hassle way to share your files, install Freenas, you can have a working server in 20 minutes, smb,ftp whatever you need.
Steve

---

