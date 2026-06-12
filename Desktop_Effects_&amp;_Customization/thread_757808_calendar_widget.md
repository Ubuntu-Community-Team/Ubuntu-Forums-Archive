---
title: "calendar widget"
date: 2008-04-17
forum: Desktop Effects &amp; Customization
---

### Post by hashi856 on 2008-04-17
I'm trying to find the calendar widget in this screen shot, or at least one that looks very similar. Anyone know where I can find it?

[http://farm1.static.flickr.com/232/498957719_7529bfe8fd.jpg](http://farm1.static.flickr.com/232/498957719_7529bfe8fd.jpg)

---

### Post by mgmiller on 2008-04-19
It is the calendar in the screenlets package.


```
sudo apt-get install screenlets
```

After install, look in Applications > Accessories > Screenlets

Once the screenlet is running, right click it to change its size and other behaviors.

---

### Post by hashi856 on 2008-04-20
> **mgmiller said:**
> It is the calendar in the screenlets package.


```
sudo apt-get install screenlets
```

After install, look in Applications > Accessories > Screenlets

Once the screenlet is running, right click it to change its size and other behaviors.

I tried it and got this message:

stephen@stephen-desktop:~$ sudo apt-get install screenlets
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package screenlets
stephen@stephen-desktop:~$

---

### Post by Saya on 2008-04-20
You need to enable the 'universe' repository in Software Sources.

---

