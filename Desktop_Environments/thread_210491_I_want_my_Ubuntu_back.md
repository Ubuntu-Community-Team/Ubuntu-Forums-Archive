---
title: "I want my Ubuntu back"
date: 2006-07-06
forum: Desktop Environments
---

### Post by rmsoldato on 2006-07-06
Having installed, and loved, Ubuntu for the first time a few days ago, I wanted to try the other flavors of it.  I install the KUbuntu-desktop packages, played around with it, and ultimately decided I liked normal Ubuntu better.  But now I have a problem, no matter what I try I can't seem to turn everything back to regular Ubuntu settings.  My startup screens are Kubuntu, my login screen is Kubuntu, shutdown is Kubuntu, default session is Kubuntu, etc.  I've tried removing the Kubuntu packages, reinstalling the Ubuntu-desktop packages, but no good.  Kubuntu has completely taken over.  I've spent the last 4 days setting up this system for the first time, and am not keen on reinstalling Ubuntu from scratch and spending the next 4 days getting back to where I am now.  Help please.  What can I do to get all my original Ubuntu browns and settings back?

-The Soldato

---

### Post by christofer.c.bell on 2006-07-07
You can get back to the normal Ubuntu desktop/install by following these instructions:

[http://www.psychocats.net/ubuntu/puregnome.php](http://www.psychocats.net/ubuntu/puregnome.php)

---

### Post by atoponce on 2006-07-07
> **rmsoldato said:**
> Having installed, and loved, Ubuntu for the first time a few days ago, I wanted to try the other flavors of it.  I install the KUbuntu-desktop packages, played around with it, and ultimately decided I liked normal Ubuntu better.  But now I have a problem, no matter what I try I can't seem to turn everything back to regular Ubuntu settings.  My startup screens are Kubuntu,

Called usplash.  Check out this [wiki post]("https://help.ubuntu.com/community/USplashCustomizationHowto") regarding that topic.

>  my login screen is Kubuntu, shutdown is Kubuntu, 
This is because you have KDM running rather than GDM.  This can be fixed with pulling up the terminal and typing:

```
sudo dpkg-reconfigure gdm
``` 
> default session is Kubuntu, 
When logging in, click on "Select Session", choose "Gnome" and click "Make Default" 

> I've tried removing the Kubuntu packages, reinstalling the Ubuntu-desktop packages, but no good. 
Hopefully, when you installed it, you used aptitude, and not apt-get.  From here on out, when you see anyone on these forums telling you to use 'apt-get', substitute it with 'aptitude'.

---

### Post by rmsoldato on 2006-07-07
Thank you so much.  Everything is back to original with much less trouble than reinstalling everything.

---

