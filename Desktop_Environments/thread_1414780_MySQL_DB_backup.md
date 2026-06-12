---
title: "MySQL DB backup"
date: 2010-02-24
forum: Desktop Environments
---

### Post by raunhar on 2010-02-24
How do i take a backup of MySQL database on local PC. I use phpmyadmin to create them.
I want to take the backup of complete folder rather than through PHPMYADMIN

Pl. Suggest

---

### Post by DaithiF on 2010-02-24
check out mysqldump

something like:
```
mysqldump -h host -u username -ppassword database > /path/to/database.dump
```

---

### Post by Jeff Anthony on 2010-02-24
Look under the hood of the Export tab in phpmyadmin. There is a web-GUI for backup and restoration.

---

### Post by raunhar on 2010-02-24
I need to know the path to MySQL folder whre all the databases are stored as a sql file, just like /var/www is the folder for the localhost websites

---

### Post by Jeff Anthony on 2010-02-25
I haven't used it in a long time but isn't there a spot where you tell it where to save to?

---

### Post by raunhar on 2010-02-25
When we create a databse, it creates a sql file in some folder.
Which is this folder and how can I just copy the sql from this folder to my backup folder.

---

### Post by raunhar on 2010-02-25
Under var/lib there is a folder mysql, which contains the databases.
How can I have access to it menas, how do I change the permissions.

---

### Post by DaithiF on 2010-02-25
/var/lib/mysql by default.

but copying files from there is not the preferred way to do mysql backups, using mysqldump as in the previous post is better.

---

### Post by Jeff Anthony on 2010-02-25
SQL is the language used to manipulate the data, it is not the structure the database uses to store data, slight difference. To turn your database into SQL format for backup and migratory purposes without going into too much detail simply use the phpmyadmin GUI.

I just installed phpmyadmin here at home so I can see what I'm describing.

1) Navigate to your phpmyadmin - mine is at [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)
2) Of the selection of tabs at the top choose "Export"
3) Choose the database(s) you want to turn into SQL-format
4) Be sure SQL is chosen
5) And on the bottom choose "Save as File", choose wherever you wish to save it to.

---

