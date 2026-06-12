---
title: "Remove Graphical &quot;gdm&quot; login"
date: 2005-05-24
forum: Desktop Environments
---

### Post by s7eam on 2005-05-24
Hello,

I'm new to Ubuntu and I am impressed that this distribution found all of my hardware on my hp laptop. It's incredible. But I would like to remove this Gnome X login. I tried to edit inittab but it doesn't help. Does anyone here have suggestions how to change it so I can login with old style login at the console?

Thanks in forward.

---

### Post by s7eam on 2005-05-24
So, no one have solution on this? hum... :neutral:

---

### Post by Staesys on 2005-05-24
Google says that this:

```
update-rc.d -f gdm remove
``` 

Will do what you want, but don't take my word for it, and I refuse to accept any responsibility if it hoses your system.

I found this info from:

[http://mail.gnome.org/archives/gnome-list/2004-September/msg00108.html](http://mail.gnome.org/archives/gnome-list/2004-September/msg00108.html) 

-Paul

---

### Post by s7eam on 2005-05-24
Thanks alot. I will test it. It doesn't metter if it hoes my system, I don't have any important data on it yet. I'll come back here and tell you if I succeeded.

---

### Post by Xian on 2005-05-24
Use the first command to disable GDM and get a console prompt instead.
Use the second command to enable GDM again.

This way you can basically just toggle it on and off.

```
$ sudo mv /etc/rc2.d/S13gdm /etc/rc2.d/s13gdm
```
```
$ sudo mv /etc/rc2.d/s13gdm /etc/rc2.d/S13gdm
```

---

### Post by s7eam on 2005-05-24
Thank you guys for help. It's not so easy to find all those stuff when you come from Slackware background. 

This command worked fine.
```
update-rc.d -f gdm remove
``` 

I booted into singel-user mode ran the command above and changed back to multi-user mode. Rebooted the machine and it worked fine.  :)

Now I will do what you said Xian but I have to install gdm first. This is good training for newbe on Ubuntu.

---

