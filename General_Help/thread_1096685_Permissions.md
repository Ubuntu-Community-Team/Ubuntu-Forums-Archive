---
title: "Permissions"
date: 2009-03-15
forum: General Help
---

### Post by gdn1947 on 2009-03-15
Have copied a Windows programme to my home folder and it appears as read only. Now want to delete it but cant do so as Permission denied. What do I have to do to obtain the necessary permissions to allow the deletion? Thanks

---

### Post by gdn1947 on 2009-03-15
Have copied a Windows programme to my home folder and it appears as read only. Now want to delete it but cant do so as Permission denied. What do I have to do to obtain the necessary permissions to allow the deletion? Thanks

---

### Post by konqueror7 on 2009-03-15
```
sudo rm <filename>
```
just be careful on what you delete...;)

---

### Post by wjp.reg on 2009-03-15
> **gdn1947 said:**
> Have copied a Windows programme to my home folder and it appears as read only. Now want to delete it but cant do so as Permission denied. What do I have to do to obtain the necessary permissions to allow the deletion? Thanks

from the terminal, you use the remove command - **rm**, as Super User.

```
sudo rm [file]
```

---

### Post by binbash on 2009-03-15
delete it via opening nautilus as root (gksudo nautilus) or delete it at terminal via adding sudo (example : sudo rm -rf /home/USERNAME/Desktop/DELETEFOLDER )

---

### Post by gdn1947 on 2009-03-15
Thank you

---

### Post by gdn1947 on 2009-03-15
Thank you

---

### Post by bodhi.zazen on 2009-03-15
Moved to General Help.

See also :

[FilePermissions - Community Ubuntu Documentation]("https://help.ubuntu.com/community/FilePermissions") 

[RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo")

---

### Post by bapoumba on 2009-03-16
Threads merged.

---

