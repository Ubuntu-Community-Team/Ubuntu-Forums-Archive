---
title: "Create new admin user"
date: 2009-03-20
forum: General Help
---

### Post by mnelson07 on 2009-03-20
I am trying to setup a test box for an employee here who wants Linux. Upon installing Ubuntu, I setup my own account and now I want to create a separate account. I tried to do it through the interface System > Administration > Users and Groups but all the options are grayed out. Here is an example of what I've tried in the terminal:

```

sudo useradd testuser -m -p password

```

It does create the testuser and it creates a home directory... but I can't login using the password I thought I designated.

Any ideas/help?

Thanks!

*EDIT*
Ah, I'm dumb. If you do this:
```

sudo useradd user

```
Ubuntu (that is v8.10) creates the home directory and prompts for a password and any other info.

---

### Post by Nano_ext3 on 2009-03-20
See:  [http://ubuntuforums.org/showthread.php?t=541087](http://ubuntuforums.org/showthread.php?t=541087)

```
sudo nano -Bw /etc/group
```


Cheers!

_Nano

---

