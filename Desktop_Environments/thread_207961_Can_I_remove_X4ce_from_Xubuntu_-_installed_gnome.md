---
title: "Can I remove X4ce from Xubuntu - installed gnome"
date: 2006-07-02
forum: Desktop Environments
---

### Post by Kilz on 2006-07-02
I setup a small file server that is also my Direct Connect hub. I needed a gui because I leave valknut running on the hub 24/7. I originally thought it would be nice to use xfce as it was suggested it was lighter so I installed Xubuntu. But I found I don't really like xfce, it just isn't for me. 
I installed gnome with apt-get install ubuntu-desktop. But I don't like how the menu is all mixed up with xfce things. Can I safely remove xfce with apt-get remove xubuntu-desktop ? Will gnome still work? Or will taking the original desktop out cause problems?

Thanks
Kilz

---

### Post by Jagot on 2006-07-02
Look at the bottom of this page:

[http://psychocats.net/ubuntu/puregnome.php](http://psychocats.net/ubuntu/puregnome.php)

apt-get remove xubuntu-desktop will just remove the metapackage - it will not remove all components associated with that metapackage.  In future you may want to use aptitude to perform such actions as it handles dependencies better than apt-get

---

### Post by Kilz on 2006-07-02
[QUOTE=Jagot]Look at the bottom of this page:

[http://psychocats.net/ubuntu/puregnome.php](http://psychocats.net/ubuntu/puregnome.php)

apt-get remove xubuntu-desktop will just remove the metapackage - it will not remove all components associated with that metapackage.  In future you may want to use aptitude to perform such actions as it handles dependencies better than apt-get[/QUOTE]
Thanks for the link, yes , I will keep aptitude in mind. But I knew I would like gnome as it was on my main desktop, so Im not ever palning to remove it. Xfce came preinstalled on Xubuntu so aptitude wasnt an option. 
So I can do it without disrupting gnome?

---

### Post by Jagot on 2006-07-02
Yep - that will remove everything that GNOME does not rely on, so you can go ahead with it.

---

### Post by Kilz on 2006-07-02
Thanks, it went pretty smooth. Until I saw that it also uninstalled Apache and a few other things I had installed. I think they were all installed while I was using Xfce. Not a biggie, it only took an hour of troubleshooting, php wouldn't work. Finlay went into sytaptic and did complete removals, then reinstalled. As long as gnome kept working I count it as a success. Im still not 100% comfortable with the cli when trouble rears its ugly head.

---

