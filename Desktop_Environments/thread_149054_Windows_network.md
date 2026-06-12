---
title: "Windows network"
date: 2006-03-23
forum: Desktop Environments
---

### Post by shaan_l on 2006-03-23
Hi again!

I did a server install, and I need to access a windows network which has shares on it.

How do I do this? I installed samba and krusader, however krusader says it doesnt support the protocol.

---

### Post by Jason_25 on 2006-03-23
```

man smbclient

```

---

### Post by stefanr on 2006-03-23
Well, you can browse the network in Konqueror using a url like

smb:/

Any shares that need mounting at boot you can specify in /etc/fstab with fstype cifs.

---

### Post by shaan_l on 2006-03-23
cool thanks!

what i have also done is create a fat32 partition, so myself and the windows users can share stuff in a central place.

i try sharing the location, and its all greyed out! also, in root mode it doesn't save any settings! did i do something wrong?

---

### Post by jturnbul on 2006-03-26
[QUOTE=stefanr]Well, you can browse the network in Konqueror using a url like

smb:/

Any shares that need mounting at boot you can specify in /etc/fstab with fstype cifs.[/QUOTE]

OMG, thats amazing.  I used that command, and I instantly had access to my xp machine, and every file in it.  I cant even get my XP on my laptop to have access like that.  Just goes to show how insecure windows is.  Hopefully no one ever cracks my network with a linux box.

The funny thing is a set my XP desktop up so that only specific users would have access to my XPdesktop.  So much for that.

---

### Post by LinuxAtLast on 2006-03-29
When I do smb:/ I can see all the computers on my windows domain, however I can't access any of them. I type in the correct user name and password, but the login box just comes back ](*,)  Is this because it is a domain? Is there a way of joining my Kubuntu box onto the domain (hosted on a windoze 2000 server)?

Thanks, Geoff

---

### Post by ipstone on 2006-06-01
I have the same problem 
typed in the right network address , usrname/pass, but the windows prompt back again asking for password

In the past I don't have this problem using suse linux, is there something wrong here? (I am using dapper)

maybe the network authentation methods implemented in ubuntu doesn't support the network? 

need your help!

---

### Post by s31523 on 2006-06-01
Did you set up the samba password file?

i.e. sudo smbpasswd -a <user>

---

### Post by klchan on 2006-06-08
[QUOTE=LinuxAtLast]When I do smb:/ I can see all the computers on my windows domain, however I can't access any of them. I type in the correct user name and password, but the login box just comes back ](*,)  Is this because it is a domain? Is there a way of joining my Kubuntu box onto the domain (hosted on a windoze 2000 server)?

Thanks, Geoff[/QUOTE]


I'm having the same problem as well on the 6.06. I manage to setup samba and let xp machine to get files from ubuntu, but not the other way around and i'm using them in the domain as well. I've been searching around for the solution, but the reply just ended here with no solutions ..... ?

---

### Post by khorjak on 2006-06-22
When prompted for your username, try it with the domain name as well, 
eg. windomain\johnny
where windomain is your Windows domain name and johnny is your username.

---

### Post by Al3xanR0 on 2006-06-22
[QUOTE=LinuxAtLast]When I do smb:/ I can see all the computers on my windows domain, however I can't access any of them. I type in the correct user name and password, but the login box just comes back ](*,)  Is this because it is a domain? Is there a way of joining my Kubuntu box onto the domain (hosted on a windoze 2000 server)?

Thanks, Geoff[/QUOTE]

try smb://hostname or ipaddress/c$

make sure that when you attempt to establish connection that the c$ (default share) is enabled. If you are logging on to a domain when you are prompted for authentication credentials replace workgroup with domain name. You may also wnat to Kde Control Center-> Internet and Network-> Local Network Browsing and add those credentials there.

---

