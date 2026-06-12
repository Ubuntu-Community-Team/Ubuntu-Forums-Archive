---
title: "Samba Server"
date: 2005-11-21
forum: Desktop Environments
---

### Post by CharlieC on 2005-11-21
All I want to do is to get my XP Home machine to see my Ubuntu 5.10 machine. I have managed to do the reverse which is to have Ubuntu see XP. I can even put a file in the XP shared folder but XP will not see Ubuntu. I have read all the directions I could find and nothing seems to work. I even made a public folder that could be shared as the directions indicated. Could someone give me some clues as to what I am doing wrong and where to find the information to correct it.
    I was able to do this on SUSE 10.0. Adding a share was easy in YAST. Here is my smb.conf:
[Network]
path = /home/cc/Network
available = yes
browseable = no
public = yes
writable = yes

[public]
   comment = Public Folder
   path = /home/public
   public = yes
   writable = yes
   create mask = 0777
   directory mask = 0777
   force user = nobody

  force group = nogroup

available = yes
browseable = no

    I am not sure if I should change the browsable to "yes". I am a relative newb far from a Linux geek. So far I have managed to get this far by reading directions, googling and asking in forums. 

Charlie

---

### Post by casper_2095 on 2005-11-21
This works for me with XP... (set your 'hosts allow' as approriate)

```

## permit local network only; map unrecognised users to 'guest' account
[global]
	log file = /var/log/samba/log
	log level = 1 passdb:2 auth:2 winbind:2
	server string = foobar
	hosts allow = 192.168.
	map to guest = Bad User
	guest account = guest
	veto files = /lost+found/;
	hide unreadable = yes

## file dump for anyone and everyone.
[store]
	path = /store
	guest ok = yes
	writeable = yes

```

Watch your log file.  
eg: 
tail -f /var/log/samba/log 

Check the directory and file permissions on the directory. 
eg:  
sudo chown root:root /store
sudo chmod 775 /store

---

### Post by CharlieC on 2005-11-21
Thanks for your reply. 
I added the lines you suggested to my /etc/hosts.allow
In the IP address I put 192.168.1.101 which is the machine IP address. 
I checked the /var/log/samba/log and I see that my machine name is wrong. I changed it from linuxfour to linuxthree, the log has linuxfour and the IP. 
As far as the permissions, I dont know what you want me to change the permissions on.
Sorry to be so dense but I am sort of a newb.

Thanks
Charlie

---

### Post by casper_2095 on 2005-11-21
Sorry.  No.  That's my /etc/samba/smb.conf there. Nothing to do with /etc/hosts.allow.  It's a fairly minimal smb.conf which I'd hoped you could work from.
You'll have to find yourself a samba howto and work through it.

This might help?
[http://ubuntuguide.org/#sambaserver](http://ubuntuguide.org/#sambaserver)
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html)

---

### Post by CharlieC on 2005-11-22
Thanks again for the reply. I read everything you suggested, and made some modifications to smb.conf.
Now at least the Ubuntu machine named linuxthree is seen by the ubuntu machine but not by windows, yet. 
    When I click on the icon named linuxthree it asks me for a password. I give my root password and it does not take it and wont let me in. It reads user name which is my regular user name   charlie   then it has domain, and reads workgroup, I don't know if that is correct and the last line is password and it will not take any password I have assigned to the syste.
    Any suggestions on how to fix that?

Charlie

---

