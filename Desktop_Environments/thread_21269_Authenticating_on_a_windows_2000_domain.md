---
title: "Authenticating on a windows 2000 domain"
date: 2005-03-21
forum: Desktop Environments
---

### Post by battletux on 2005-03-21
Hi,

Can anyone help i need my warty install to auth. on a Win 2k network. I have installed samba and smbfs. I have enabled windows networking, i acn see all PC's on the network but can not connect. Also i can not login to the network, only the local machine. I have admin rights on the network, so it's just configuring the machine to connect and authenticate. I think this is also the reason why evolution can not connect to our exchange server.

I'm pretty new to this so please bear with me.

Anyone know of some Ubuntu guides to do this or have any advice?

---

### Post by cwaldbieser on 2005-03-22
What is it exactly you are trying to accomplish?  Do you just want to access shares on Win2K machines from your Ubuntu machine, or do you want to have your Ubuntu machine act as a file/print server for the Windows machines, or something else?

I can access the shares on my Win2K box from ubuntu by giving a URL like
```
smb://DOMAIN\User@IP-Address/$C
```
(have done this in Kubuntu in konqueror-- I have done something similar under Ubuntu with nautilus).

Any extra explanation as to what you are trying to acheive could be helpful.

---

### Post by battletux on 2005-03-22
I was wanting to access the windows shares, by going through the 'Network' window under system.

I just can not get it working on Warty, so upgraded to Hoary last nite and it works a treat. It even fixed the issue i had with lines on the x display.

---

