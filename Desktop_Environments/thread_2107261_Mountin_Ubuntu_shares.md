---
title: "Mountin Ubuntu shares"
date: 2013-01-21
forum: Desktop Environments
---

### Post by brent1975 on 2013-01-21
Hello I am currently trying to mount a few shares on my Ubuntu Desktop and having a bit of a problem 

I have a Ubuntu 12.04 server sitting in the basement that houses all my media, documents etc...  

I have a desktop that has Ubuntu 12.04 and I am able to connect to the share manually using the connect to server method.  So I was wanting to mount these specific drives so that they would be there even after I reboot the computer.

I did some reading and came up with this method.

I installed samba from the appstore.
I created a few folders in /media called brent,music,movies,www
I opened up /etc/fstab and modified it with adding the following at the bottom

```
//192.168.2.105/Movies /media/movies smbfs credentials=/etc/samba/cred-file,uid=brent,gid=users 0 0

//192.168.2.105/Music /media/music smbfs credentials=/etc/samba/cred-file,uid=brent,gid=users 0 0

//192.168.2.105/Brent /media/brent smbfs credentials=/etc/samba/cred-file,uid=brent,gid=users 0 0

//192.168.2.105/WWW /media/www smbfs credentials=/etc/samba/cred-file,uid=brent,gid=users 0 0
```I then created a file in /etc/samba/cred-file and made my credentials.

[HTML]username=brent
password=mypassword[/HTML]
saved and did a sudo mount-a from terminal and I get 4 password prompts each time I put in the password a drive will mount. 

I am used to putting in a password when ever I do anything sudo related but 4 times for each drive seem something is messed up.... 

I have tried this on a windows box and mounts fine. so I know its not something wrong with my samba server with permissions. It seems that it is not seeing the cred-file for some reason.  Any one have an Idea. Open for Ideas or suggestions..

Thank you in advance,

--Brent



This has not been resolved. Took the liberty of solving this and creating one in the Network section.

---

