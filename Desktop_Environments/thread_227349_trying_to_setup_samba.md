---
title: "trying to setup samba"
date: 2006-08-01
forum: Desktop Environments
---

### Post by ubiwankanubi on 2006-08-01
so far, this is what I've done:
1. installed samba via synaptic.
2. I can see and mount a folder shared on a windows computer from linux.
3. the windows computer can see linux, but can't access it.
4. I created a user account in linux with the same user name and password of the windows machine.
5. still can't connect windows to linux.

any idea what I missed when setting things up?

---

### Post by apjone on 2006-08-01
as root do 
smbpasswd *username*

this will set up a samba user that you can use to connect to the linux box

---

### Post by apjone on 2006-08-01
also edit /etc/samba/smb.conf 

and add the following at the bottom and restart /etc/init.d/smbd

[sharename]
path = path to share
comment = descritpion of share
available = yes
browseable = no
public = yes
writable = yes

---

