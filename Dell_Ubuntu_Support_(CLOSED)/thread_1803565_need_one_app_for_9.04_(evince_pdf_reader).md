---
title: "need one app for 9.04 (evince pdf reader)"
date: 2011-07-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Jon_J on 2011-07-13
I know I should be using the newer kernel version, and I am.
I have a Dell mini-10 with the darned poulsbo graphics.
I have 5 OS's in multi-boot and xubuntu 9.04 is my favourite for just surfing the web and playing aisleriot solitaire (with sounds).
9.04 has the best speed of all the below.
Browsing the net in firefox in the other 4 OS's lags and stumbles.
In 9.04 using firefox, browsing and scrolling is smooth and quick.
The 5 systems I multiboot are:
windoze xp
xubuntu 9.04
jolicloud 1.2 (latest, based on 10.04 and 10.10, I think)
debian 503+lxde squeeze
xubuntu 10.04
I just need an older archive containing evince compiled for 9.04 (I have all the depends, libs etc).
Any hints where to search? thanks in advance.

---

### Post by snowpine on 2011-07-13
The repositories for 9.04 have been moved to [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com)

Update your software source mirror and then you can install evince using apt-get/synaptic/add-remove software.

---

### Post by Jon_J on 2011-07-13
Thank you for your quick response.
Do I need to input the complete path to the packages?
When I added "deb" "http://old-releases.ubuntu.com" "jaunty" to the GUI without the quotes, I keep getting errors.
I added this under 3rd party sources tab. There is no place to add it to the main tab, "Ubuntu Software"

Or should I edit /etc/apt/sources.list  ?

---

### Post by snowpine on 2011-07-13
```
gksu gedit /etc/apt/sources.list
```

Change all of the mirrors to old-releases, for example change this:

```
deb http://us.archive.ubuntu.com/ubuntu/ jaunty main 
```

to this:

```
deb http://old-releases.ubuntu.com/ubuntu/ jaunty main 
```

Now you can use:

```
sudo apt-get update
sudo apt-get install evince
```

or your favorite GUI package management tool.

---

### Post by Jon_J on 2011-07-13
Thank you, that did what i needed.:)
Jon_J

---

