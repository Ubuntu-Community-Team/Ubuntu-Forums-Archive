---
title: "Samba and Windows XP"
date: 2006-06-24
forum: Desktop Environments
---

### Post by UrbanLegend on 2006-06-24
I am trying to make a few folders on Ubuntu be shared and after I do so and use the same domain as Windows XP I can see, but cannot actually connect to the other computer. I tried logging in with the same username and password as I use in ubuntu, but that still does not work.

Any and all help is appreciated.

EDIT the message I get when trying to map it is that it isn't accessible and I might not have permission to access this resource.

---

### Post by raptros-v76 on 2006-06-24
change the security setting in /etc/samba/smb.conf to share, and dont give a username or password when connecting

---

### Post by UrbanLegend on 2006-06-24
Gah. I still can't get this to work.

---

### Post by raptros-v76 on 2006-06-24
you know what? use apache2 and make a http server
sudo aptitude install apache2
 then make a directoy of all of the stuff you want to share, and then
sudo ln -s <whatever the directory is of the shared stuff> /var/www/ 
then go to http://<whatever your ubuntu computers name or ip address is>

---

