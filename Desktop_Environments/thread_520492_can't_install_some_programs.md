---
title: "can't install some programs"
date: 2007-08-08
forum: Desktop Environments
---

### Post by yf1208 on 2007-08-08
whenever i try to install a new program or update,i keep getting this error message

[[IMG]http://img472.imageshack.us/img472/2215/screenshotjw8.th.png[/IMG]](http://img472.imageshack.us/my.php?image=screenshotjw8.png)

something to do with synaptic?
I can't find the program anywhere in the update manager part

---

### Post by ruibernardo on 2007-08-08
Hi Yf1208,

you can't install programs because you are using an account that is not an admin account (the first account you create when you instal Ubuntu).

Add yourself to the "admin" group or give you some rights on the file /etc/sudoers ([https://wiki.ubuntu.com/Sudoers](https://wiki.ubuntu.com/Sudoers)). 

Of course, you have to be in the admin account to do this.

---

### Post by yf1208 on 2007-08-08
my account is mess up,since i made some mistake while installing and i have to use recovery mode to create a new id and pass.

how do i add the account i'm using right now to admin group?

---

### Post by ruibernardo on 2007-08-08
I would advise you to reinstall. If you can't or don't want, there is a "hard way". 

Check what is your id with:

```
id

```This should say what's your gid ("**gid=1000(your_groupname)**" or similar).

Boot the computer using a LiveCD (Ubuntu Desktop CD will do it). 

Mount the Ubuntu partition (click the Gnome menu in "Places", then in "Computer" and then click in the partition, it should be mounted in "/media/disk" directory).


Open a terminal (Applications, Accessories, Terminal), and type

```
sudo -i
cd /media/disk/etc/

nano group
```Add your groupid (the one you found when you did "id") in the "admin" group (the line that says something like "**admin:117:groupid_name**").

If you want you can replace the one that's there by the new one.

Save & exit nano editor with Ctrl+x and pressing Y.

This isn't guaranteed to work (might need to reboot). Again, I must advise you to try to reinstall to have a "healthy" system.

---

### Post by yf1208 on 2007-08-08
thanks

i reinstall it instead,fixed everything

another question here

Since i installed Ubuntu on a partition portion of a bigger Hard Disk,how do write/edit all those files that are "outside"?

Instead of booting up windows to edit it,is there any way to do it in ubuntu?

It keeps showing up the "you do not have permission" error  message

---

### Post by ruibernardo on 2007-08-08
If you're talking about NTFS partitions, yes you can. Install the package "ntfs-3g".

---

### Post by yf1208 on 2007-08-08
thanks,it worked

---

