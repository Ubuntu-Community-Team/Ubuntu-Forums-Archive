---
title: "Xorg problem and so on..."
date: 2005-05-26
forum: Desktop Environments
---

### Post by smilelover on 2005-05-26
Hi frieds,
i'm thinking about leaving Slackware (various reasons) and I was quite attracted by Kubuntu so I installed it.

however, I encoutered a few problems...

1. When starting X, my monitor always cries that the desired mode is out of range (Kubuntu tries some 101Hz in 1280x1024)...I have to reset X (Ctrl+Atl+Bckspc) in order to see KDM... This issue does not have anything to do with xorg.conf, I think. I copied my 100% working Slackware xorg.conf to my Kubuntu and the problem remained...
Kubuntu never showed me [this screen](http://shots.osdir.com/slideshows/306/27.gif) 
It just gave me the command line and told me I can enter "exit" in order to get back to some setup program or so... and "exit" did nothing

2. How do I enable/disable the services Kubuntu starts when booting? What if I wanted to switch off HAL, DBUS, SAMBA or enable/disable apache, mysql...

3. Where do I get a bootsplash for Kubuntu similar to [Ubuntu one](http://www.bootsplash.de/files/themes/screenshots/Theme-Ubuntu-silent.png)

---

### Post by deadlands on 2005-05-26
I can help with number 3

[http://kde-look.org/content/show.php?content=22695](http://kde-look.org/content/show.php?content=22695)

---

### Post by NTolerance on 2005-05-26
2.  ```
sudo apt-get install rcconf
sudo rcconf
```

and uncheck the services you don't want.

---

### Post by smilelover on 2005-05-27
thanx for the replies, guys...

---

### Post by dresnu on 2005-05-27
You can also check webmin ([www.webmin.com](www.webmin.com)) for services and alot of other system settings. You can find it in the universe repository.

---

