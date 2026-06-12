---
title: "can see ubuntu machine but cant see my samba share"
date: 2006-01-09
forum: General Help
---

### Post by dus10 on 2006-01-09
I can see my ubuntu machine from my windows pc but it asks for a username and password. I put in my username and password that I use to login to the ubuntu machine but I cant access the location that I set up as a samba share; it gives an error. How do I access that share now?  I set up a folder to share but I cant get in. 

I'm a "linewbie", so I'll take all the direction I can get.

---

### Post by casper_2095 on 2006-01-09
$ man smbpasswd


Samba will take user/passwords from a variety of places.  If you just want to link it to the login id's (/etc/passwd) I'm sure it will do that with the right options in your /etc/samba/smb.conf

---

### Post by manicka on 2006-01-09
This may also help

[http://doc.gwos.org/index.php/Share_files_using_Samba](http://doc.gwos.org/index.php/Share_files_using_Samba)

---

