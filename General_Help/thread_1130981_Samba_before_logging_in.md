---
title: "Samba before logging in"
date: 2009-04-20
forum: General Help
---

### Post by gloscherrybomb on 2009-04-20
Is it possible to have samba shares available before I log in?

Specifically, I have a 2nd hard drive which stores all of my media, movies music etc. and would like to be able to access it over the network just by turning on the pc and before I log in.

Ubuntu 8.10 

Thanks

---

### Post by nikgare on 2009-04-20
You will need to add a line to fstab for each share, this will then mean that this is mounted at boot time.
Here is a line from my fstab which works for me (change USERNAME and PASSWORD):

```
//192.168.1.10/photos    /media/photos        cifs    username=USERNAME,password=PASSWORD,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

This is probably a bit insecure for most uses apart from local use due to the visible password.

---

### Post by gloscherrybomb on 2009-04-20
Thanks. If I don't have a username and password is it OK to leave that bit out?

(I allow guest access for my shares)

---

### Post by nikgare on 2009-04-20
Not really sure, but much more info is here:

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

---

