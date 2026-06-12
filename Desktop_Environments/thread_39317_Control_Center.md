---
title: "Control Center"
date: 2005-06-04
forum: Desktop Environments
---

### Post by spednik on 2005-06-04
Ok, just have a first quick question before the main one, what is Kubuntu's default fonts? 

Now for the hard one. Last  night , i messed up my passwords, and based on some help from people here, managed to do something in grub and now i am in single user mode. Now whenever I go into control center, and try and do something where you need to click "administrator mode" it just brings me back to the main control center screen whenever i press it, so i cant do anything serious really in control center. 

Thanks in advance for any help.

---

### Post by Seti on 2005-06-04
Probably because by default all the admin stuff is done with sudo; do do what you want to do, you have to first:

1) Open a console and type```
sudo passwd
```. Then enter your user password. It will prompt you for a password, this will be the root password.

2) Type in a good password. It will then prompt you to confirm it.

The admin password you have set should now work in Kontrol centre.

---

### Post by shakin on 2005-06-04
When in single user mode you need to change your user's password:
```

$ passwd {username}

```

Then go back into grub's menu.lst and remove the 'single' word from the boot line so when you reboot you'll be back into multiuser mode. Now reboot and login with your new password.

---

### Post by SGC on 2005-06-04
Kubuntu's defualt font is Bitstream Vera Sans

---

### Post by J.Miller on 2005-06-04
In console run

sudo kcontrol

.

---

### Post by spednik on 2005-06-04
Thanks, i tried sudo kontrol and it worked, but it gave me a bunch of errors

spednik@CPE000d56a81d40-CM00e06f1b1d1a:~$  sudo kcontrol
Password:
Error: "/var/tmp/kdecache-spednik" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
ERROR: Communication problem with kcontrol, it probably crashed.
spednik@CPE000d56a81d40-CM00e06f1b1d1a:~$ Error: "/tmp/ksocket-spednik" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/ksocket-root"
Error: "/var/tmp/kdecache-spednik" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-spednik" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Error: "/var/tmp/kdecache-spednik" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Link points to "/var/tmp/kdecache-root"
Error: "/var/tmp/kdecache-spednik" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image

But it worked, so  I guess the errors are nothing serious. Thanks all. :)

---

### Post by Jonathan2007 on 2005-06-04
[QUOTE=spednik]Thanks, i tried sudo kontrol and it worked, but it gave me a bunch of errors

spednik@CPE000d56a81d40-CM00e06f1b1d1a:~$  sudo kcontrol
Password:
Error: "/var/tmp/kdecache-spednik" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
ERROR: Communication problem with kcontrol, it probably crashed.
spednik@CPE000d56a81d40-CM00e06f1b1d1a:~$ Error: "/tmp/ksocket-spednik" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/ksocket-root"
Error: "/var/tmp/kdecache-spednik" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-spednik" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Error: "/var/tmp/kdecache-spednik" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Link points to "/var/tmp/kdecache-root"
Error: "/var/tmp/kdecache-spednik" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image

But it worked, so  I guess the errors are nothing serious. Thanks all. :)[/QUOTE]

For some apps you need to use kdesu instead of sudo. You may have to have the root account enabled to be able to use kdesu. Look on ubuntuguide.org for info on how to enable the root account. Then just use kdesu wherever you were using sudo. So the command would then be kdesu kcontrol. Oh and try searching about your kcontrol problem as some people have found that if you delete a certain file then kcontrol will allow the administrator mode button to work correctly again for a while.

---

### Post by spednik on 2005-06-04
I actually have a new problem, unrealated to this one, but i figured it would be better to use the same thread, as to take up less space, so here goes. 

For some reason earlier today, my X (i think it would be that) started getting...well, wierd. The fonts kind of look strange, and my screen wont really show straight lines....The desktop mostly looks fine, thats the most mild part, execpt the icon fonts suddenly changed, to a darkish colour, i didnt change them

I don't know how to describe it really well, so I took some screenshots, if i can get them posted up here..
[IMG]http://img.photobucket.com/albums/v171/spednik/snapshot1.png[/IMG] 


Hope that works, i couldnt seem to get a screenshot of the Menus, but there very bad, almost unreadable. 

Thanks in adavance (again.)

---

