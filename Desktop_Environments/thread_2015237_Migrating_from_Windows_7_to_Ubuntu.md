---
title: "Migrating from Windows 7 to Ubuntu"
date: 2012-07-02
forum: Desktop Environments
---

### Post by viral007in on 2012-07-02
I am new to Ubuntu Linux 12.10. I would like understand file/directory structure in Linux, as I am used to Windows 7.
  I have 3 partitions basically C:, D: & E:
  
[LIST=1]
[*]C: is for system files and installed programme.
[*]D: is for my working folders like:
 d:\websites\site1
 d:\websites\site2
 d:\websites\site3
 d:\websites\phpmyadmin
 d:\mysqldata
 d:\accounts\invoices
 etc
[/LIST]
  Please guide me to migrate my system to Ubuntu desktop, as I hook to Ubuntu GUI which is pretty easy to operate.
  How do I achieve this type of directory structure in Ubuntu

---

### Post by papibe on 2012-07-03
Hi viral007in. Welcome to the forums!

You can have different partitions very similar to Windows, but they are all mounted into the hierarchical filesystem.

The system partition would be mounted at root (/). That would be the equivalent of C:

Your personal data partition it is usually mounted on /home.

Another working partition could be mounting on its own directory like /data or /home/youruser/data.

Does that help a little?
Regards.

---

### Post by viral007in on 2012-07-03
Ok I got your point.
point 1 & 2 solve my problem
Point 3 is where I more interested to know more
I have partition which is empty 150GB size
which I want to use as DATA storage like

/datat/www/site1
/data/www/site2
/data/accounts/

But will /data partition restricted to me or it can be accessed like any other folder like we have in windows D:\folders


> **papibe said:**
> Hi viral007in. Welcome to the forums!

You can have different partitions very similar to Windows, but they are all mounted into the hierarchical filesystem.

The system partition would be mounted at root (/). That would be the equivalent of C:

Your personal data partition it is usually mounted on /home.

Another working partition could be mounting on its own directory like /data or /home/youruser/data.

Does that help a little?
Regards.

---

### Post by msammels on 2012-07-04
Partitions are not restricted to a particular user, unless permissions are set. Any user on the system can mount any partition. You can, however, restrict data on the partition to a specific user/group.

---

### Post by robtygart on 2012-07-04
Yes you can access all of your drives, and partitions, and use them as storage drives.

> Please guide me to migrate my system to Ubuntu desktop, as I hook to Ubuntu GUI which is pretty easy to operate.
How do I achieve this type of directory structure in Ubuntu

Also in Linux it will read as sda/sdb/sdc

So drive 1 is sda if you have a partition it will be sda1 and sda2 and so on.

---

