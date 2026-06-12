---
title: "File/Folder Ownershi"
date: 2009-01-18
forum: General Help
---

### Post by iEthan on 2009-01-18
So, I need to change the permissions for filesystem, but it tells me I'm not the owner. I set up the computer. How would I become the owner?

---

### Post by snova on 2009-01-18
Depends. What are you trying to change? There's probably a reason it's not letting you...

---

### Post by iEthan on 2009-01-18
I'm trying to change it to write, read, the works. All permissions to me.

---

### Post by snova on 2009-01-18
Sorry... of what?

If "filesystem" should be interpreted as the entire system, you won't even have a functional system by the end. ;)

---

### Post by oldos2er on 2009-01-18
> **iEthan said:**
> I'm trying to change it to write, read, the works. All permissions to me.

 Before you do that, please read [http://psychocats.net/ubuntu/permissions](http://psychocats.net/ubuntu/permissions) and [http://www.linuxquestions.org/linux/answers/Security/Quick_and_Dirty_Guide_to_Linux_File_Permissions](http://www.linuxquestions.org/linux/answers/Security/Quick_and_Dirty_Guide_to_Linux_File_Permissions)

---

### Post by theWrkncacnter on 2009-01-18
The system is designed so that critical system files are protected from ordinary users. You can still edit them when need be by becoming the superuser. For example "sudo nano /etc/X11/xorg.conf" would edit the root-owned config file.

If there really are files you want to be writeable by ordinary users, you can use the chown command.

---

### Post by iEthan on 2009-01-19
Yes, I need to do this for folders. I have LAMP so I definitely need write access, delete access.

---

### Post by snova on 2009-01-19
> **iEthan said:**
> Yes, I need to do this for folders. I have LAMP so I definitely need write access, delete access.

As in, /var/www?

Well, I don't know whether this is considered a bad idea or not (I can't imagine why), so this would do it:

```
sudo chown <user>:<user> /var/www -R
```

Makes you the owner of /var/www and everything residing underneath.

---

### Post by Titan8990 on 2009-01-19
If you change ownership of /var/www as shown above it will cause major problems with your web server as Apache no longer will be able to read/write the dir (unless given full permissions to the other group, which defeats the purpose of changing ownership).

You should do your administration as root:


sudo -i

---

