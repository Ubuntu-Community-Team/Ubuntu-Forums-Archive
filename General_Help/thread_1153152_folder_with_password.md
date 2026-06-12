---
title: "folder with password"
date: 2009-05-08
forum: General Help
---

### Post by zeker446 on 2009-05-08
hi there hi have a storage server configured with samba, i have to folder with login anonymus but the users want to create private folder in one of them, how can i make folder with passsword?



please help me 

im posting here my smb.conf file 
[global]
workgroup = WORKGROUP
security = share
server string = storage
host allow = ALL
load printer = no
log file = /var/log/samba.%m
max log sinze = 55
netbios name = STORAGE

[STORAGE_DOCUMENTOS]
    path = /media/Documentos
    public = yes
    guest ok = yes
    writable = yes 
[STORAGE_FOTOS]
    path = /media/Fotos
    public = yes
    guest ok = yes
    writable = yes


im want to create folders inside STORAGE_DOCUMENTOS, something like folder user and give it a password so only that user can acess it

---

### Post by StuartN on 2009-05-08
> **zeker446 said:**
> im want to create folders inside STORAGE_DOCUMENTOS, something like folder user and give it a password so only that user can acess it

You can not create the user permissions within the Samba configuration. You need to create the permissions on the storage server. For instance if this is a Linux machine then the subfolders would be owned by each user (chown user:group folder) with no read permission for other users (chmod goa-r). If the storage server is a Windows machine then there is no real security from anyone gaining access to the drive, although there must be ways to configure password access for a share.

---

### Post by zeker446 on 2009-05-10
storage as ubuntu 9.04 installed so  i can create folder like example then create user example and group WORGROUP then i write sudo chown WORKGROUP:example /exmple? like this?

---

