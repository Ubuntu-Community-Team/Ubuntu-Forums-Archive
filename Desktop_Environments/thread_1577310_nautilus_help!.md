---
title: "nautilus help!"
date: 2010-09-18
forum: Desktop Environments
---

### Post by bacon_user on 2010-09-18
I got this error after using this command in terminal

gksudo nautilus /var/www

```

root@house:/etc/lighttpd# gksudo nautilus /var/www
Initializing nautilus-gdu extension

(nautilus:5179): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:5179): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

** (nautilus:5179): WARNING **: Could not inhibit power management: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Name "org.gnome.SessionManager" does not exist

(nautilus:5179): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

** (nautilus:5179): WARNING **: Could not inhibit power management: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Name "org.gnome.SessionManager" does not exist

** (nautilus:5179): WARNING **: Could not inhibit power management: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Name "org.gnome.SessionManager" does not exist

(nautilus:5179): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:5179): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:5179): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:5179): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

** (nautilus:5179): WARNING **: Could not inhibit power management: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Name "org.gnome.SessionManager" does not exist


```Help please, I'm a newbie to Ubuntu.


edit

just tried this and got a new error
```
root@house:/etc/lighttpd# nautilus /var/www
Initializing nautilus-gdu extension

(nautilus:10502): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

```


All I'm trying to do is access my /var/www folder with root permission so I can create delete etc

---

### Post by clhsharky on 2010-09-18
bacon_user

Use 
```
gksudo nautilus
```
then navigate to /var/www

or
```
gksudo gedit /var/www
```
To edit /var/www

Sharky

---

### Post by KdotJ on 2010-09-18
Or copy the file to the directory via the command line. Say your files are in a folder called "myFiles" in your home folder

```
cd ~/myFiles
sudo cp * /var/www
```

---

### Post by ammofreak on 2013-01-11
Hi ):P:

Even thought this post is a bit old, I figured a little more info would perhaps help someone else.

I use the Nemo file manager, not Nautilus. Was always getting similar errors. I did not realize *sudo nemo* & *gksudo nemo* were different until I read this post.

Apparently one should use *sudo* for superuser permissions & *gksudo* for superuser permissions in invoking a GUI setting like Nemo or Nautilus.

Thanks for enlightening me!:popcorn:

---

### Post by howefield on 2013-01-11
Old thread closed.

---

