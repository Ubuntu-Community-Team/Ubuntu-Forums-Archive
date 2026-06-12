---
title: "ubuntu services"
date: 2006-01-04
forum: Desktop Environments
---

### Post by stackpoo on 2006-01-04
i am just wondering if anyone knows the easiest way to install and start services for ubuntu (gnome). hopefully it's possible to do this from the install disk as i have to use my neighbor's slow wireless connection to get to the internet from home.

-stackpoo

---

### Post by encompass on 2006-01-04
Not sure what your wanting to do... if you want to control the services that are running in your ubuntu box there is a nice program here....[http://www.ubuntuforums.org/showthread.php?t=89491](http://www.ubuntuforums.org/showthread.php?t=89491)
That may help... I use it.
But I would be a little more descriptive in your subject heading too.

---

### Post by stackpoo on 2006-01-04
i'm trying to get services like http, ftp, and mysql installed and started on ubuntu. a friend of mine told me to use apt-get to install what ever i needed via ftp. i am wondering if anyone knows if apache, mysql, and some sort of ftp and email programs are included on the install disks ubuntu sends out. if so, how do ya get 'em started. any help is appreciated.

-stackpoo

---

### Post by darth_vector on 2006-01-04
you can check. first look in /etc/apt/sources.list and make sure that the cdrom repository is not commented. it should look something like:
```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ breezy main restricted
```
to determine if a package is available do a
```
sudo apt-cache search packagename
```
if its available, you can install it with
```
sudo apt-get install packagename
```

---

### Post by stackpoo on 2006-01-04
thank you for the input, i'll give it a go later tonight.

-stackpoo

---

### Post by stackpoo on 2006-01-19
darth_vector,

your suggestions worked great, thank you.

-stackpoo

---

