---
title: "using filezila in virtual machine xp with vsftpd on the box"
date: 2009-01-06
forum: General Help
---

### Post by elixir_ on 2009-01-06
Hi,
   this is my first thread, and first of all i would like to thank all the members and staff that have created this awesome community. Ok now with the issue so I have installed Windows Xp on my virtual machine using virtual box which runs on Ubuntu. I wanted to setup ftp on my box which I did in ubuntu using vsftpd yesterday but came about a problem. Since I use Filezilla which uses passive mode I was not able to connect to my ftp through the local subnet(I did try using cmd for connecting and it did), ironically i could do the same with the external ip of my ubuntu and use Filezila. Therefore if there was a way I could work around and use the subnet rather then going through internet. 

ps: I have also setup amp on ubuntu and I can easily connect to phpmyadmin through the subnet with my xp.

---

### Post by HermanAB on 2009-01-06
Install OpenSSH-Server on Ubuntu.  Then connect to it using FileZilla with the SFTP protocol.  That way, you only use one port (22 TCP) which can be easily forwarded through firewalls.

Cheers,

Herman

---

### Post by elixir_ on 2009-01-06
Hey thanks for the quick reply, I have installed openssh and it is working like a charm however I am not able to start vsftpd and also how do I restrict ssh for local only. thanks

---

