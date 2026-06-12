---
title: "sync desktop settings"
date: 2010-03-23
forum: Desktop Environments
---

### Post by Ahmedmb on 2010-03-23
i have Ubuntu 9.10 64 on my desktop and laptop
there is any way to sync desktop and application settings ?

THX:p

---

### Post by tom4everitt on 2010-03-23
All your settings are stored in your home folders. So syncing your home folders will also sync application settings. I guess you could just configure Dropbox to sync them.

A more "linux" way to it would be to enable ssh on both machines:
sudo apt-get install openssh-server

and then sync them with the command 'rsync' which works much like cp, but it syncs instead of copying and works over a network/internet.

sudo rsync -a /home/user name-of-laptop.local:/home/user

should work if they're connected to the same network (router). If you're interested and need more detailed instructions, post back!

---

### Post by Ahmedmb on 2010-03-23
THX tom i know this way 
i'm afraid overwrite this files make any application not work

---

### Post by Ahmedmb on 2010-03-23
I do it ,
not work completely,for example AWN setting not apply. 

Any new ideas
:p

---

### Post by imblack on 2011-07-03
[https://wiki.ubuntu.com/OneConf](https://wiki.ubuntu.com/OneConf)

---

### Post by Art0 on 2012-07-02
In the new 12.04 release, there is this feature in the Software Center, where you syncronize your files between computers (File > Sync Between Computers).
I'm not sure whether this feature is also available in 9.10 release. You might want to check that out.

---

### Post by kansasnoob on 2012-07-02
> **Art0 said:**
> In the new 12.04 release, there is this feature in the Software Center, where you syncronize your files between computers (File > Sync Between Computers).
I'm not sure whether this feature is also available in 9.10 release. You might want to check that out.

Look at the date(s) ;)

You're replying to a very, very old thread. Mostly regarding unsupported versions of Ubuntu.

---

