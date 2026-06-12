---
title: "Saving failure"
date: 2009-05-08
forum: General Help
---

### Post by Imoen on 2009-05-08
I'm trying to set up mysql administrator and when I try to save the configuration I get this error:

There was an error backing up old configuration data to '/etc/mysql/my.cnf.maold'
Permission denied

I also seem to not be able to edit /etc/mysql/my.cnf by just opening the file and editing it because when I try to save the changes I get error:

The document could not be saved, as it was not possible to write to /etc/mysql/my.cnf.

Check that you have write access to this file or that enough disk space is available.

I have plenty of disk space, how do I get permission to save files on my own computer?

---

### Post by BslBryan on 2009-05-08
Hello, Imoen. :-)

You just need to change the permissions on that certain file.  Try
```
sudo chmod o+wx /etc/mysql/my.cnf
```

Tell me if that works. :-)

Best to you, and good luck.

---

### Post by Imoen on 2009-05-08
That allows me to edit the cnf file in text editor but it still fails when trying to save settings in mysql administrator. I'm pretty new to using mysql and even to ubuntu so if I can have it working where there's descriptions as to what the settings do I prefer that over me trying to not screw things up in text editing.

---

### Post by Alekz_ on 2009-05-08
Try to sudo your text editor!

Example:
```
gksu gedit /etc/mysql/my.cnf
```
for graphic interface

or

```
sudo vi /etc/mysql/my.cnf
```

for terminal

---

### Post by Imoen on 2009-05-08
That opens the file in the text editor. I would like to allow mysql administrator the ability to save changes, not to open the file in text editor. Is there a way to sudo mysql administrator?

---

### Post by davidsantosmail on 2010-01-17
Same issue here. the mysql-admin file lives under /usr/bin/mysql-admin so I just entered sudo /usr/bin/mysql-admin and now its allowing me to save the mysql.cnf file through mysql admin. however everytime I save, it gives me a warning on the terminal window: 

the option nice is not known. Please file a bug report if this is a valid option.

---

### Post by chris954 on 2010-10-14
[QUOTE=davidsantosmail;8677834]Same issue here. the mysql-admin file lives under /usr/bin/mysql-admin so I just entered sudo /usr/bin/mysql-admin and now its allowing me to save the mysql.cnf file through mysql admin. however everytime I save, it gives me a warning on the terminal window: /QUOTE]


You need to have RW access to the /etc/mysql by executing this command:
sudo chmod o+wx /etc/mysql

---

### Post by wgw on 2010-11-17
That worked for me! (I had the same problem, and should have know better...)

Thanks!

(solved!)

---

