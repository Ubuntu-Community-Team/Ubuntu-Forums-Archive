---
title: "Can't change login screen to default"
date: 2012-05-22
forum: Desktop Environments
---

### Post by jralabate on 2012-05-22
ok some how and im not to sure how but my login screen has change to:

[IMG]http://i.minus.com/j1ol9FllyNSyt.png[/IMG]

and im not sure how to change it back to the default one like this

[IMG]http://i.minus.com/jbwtENRxmH4oEM.png[/IMG]

I have tried editing /etc/lightdm/lightdm.conf and changes greeter-session= to lightdm-gtk-greeter-ubuntu but nothing please help.



[SIZE="1"]Pic's via [http://iloveubuntu.net/](http://iloveubuntu.net/)[/SIZE]

---

### Post by zombifier25 on 2012-05-22
The first screenshot looks like GDM to me. If you have installed gdm, then run
```
sudo dpkg-reconfigure lightdm
```
and choose lightdm at the choices.

---

### Post by Rodney9 on 2012-05-23
For How-To's and Information on Lubuntu

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

For  Screen-Casts on Lubuntu

[http://blip.tv/rss/bookmarks/206798](http://blip.tv/rss/bookmarks/206798)

Rodney

---

### Post by jralabate on 2012-05-24
> **zombifier25 said:**
> The first screenshot looks like GDM to me. If you have installed gdm, then run
```
sudo dpkg-reconfigure lightdm
```
and choose lightdm at the choices.


I have tried that and i have it set to lightdm and still the same thing

---

### Post by joningi on 2012-06-10
I have the exact same problem and I think it stated when I tried out KDE .... does anyone know how to change the login screen back to the default Unity-greeter ?!

EDIT:
PROBLEM SOLVED...

I removed lightdm and then re-installed it.
I editied my lightdm.conf file (/etc/lightdm/ligthdm.conf) to only have this:

[SeatDefaults]
greeter-session=unity-greeter
user-session=ubuntu

And then I installed ligthdm-gtk-greeter

Restarted, and BOOM it worked. I got the unity-greeter log in screen again!
Try it!

---

