---
title: "backports down"
date: 2005-06-28
forum: Desktop Environments
---

### Post by vanaedium on 2005-06-28
Hi 
I need to know why backports repository are down and when will they  work again.
thanx

---

### Post by ubuntu-geek on 2005-06-28
[QUOTE=vanaedium]Hi 
I need to know why backports repository are down and when will they  work again.
thanx[/QUOTE]
 Just the website was down, the actuall repo's were online. But the website is fixed now.

---

### Post by vanaedium on 2005-06-29
ok but I can't connect with these repos.
i have setted this url in synaptic

deb [http://backports.ubuntuforums.org/ubp/](http://backports.ubuntuforums.org/ubp/) hoary-extras main universe multiverse restricted 
deb [http://backports.ubuntuforums.org/ubp/](http://backports.ubuntuforums.org/ubp/) hoary-backports main universe multiverse restricted 

are they correct? or I need new ones?

thanx

---

### Post by firas on 2005-06-30
It reads on the 1st page of the backports site:

"Access to our main server has been **DENIED** to the general public because it took simply AGES to sync to our mirrors. Please select one of our [mirrors]("http://ubuntubackports.org/url.php"). Thanks!"

Use one of the mirrors on the following page :

[http://ubuntubackports.org/url.php](http://ubuntubackports.org/url.php)

---

### Post by XDevHald on 2005-06-30
[QUOTE=vanaedium]ok but I can't connect with these repos.
i have setted this url in synaptic

deb [http://backports.ubuntuforums.org/ubp/]("http://backports.ubuntuforums.org/ubp/") hoary-extras main universe multiverse restricted 
deb [http://backports.ubuntuforums.org/ubp/]("http://backports.ubuntuforums.org/ubp/") hoary-backports main universe multiverse restricted 

are they correct? or I need new ones?

thanx[/QUOTE]

I see that they're up, but you can add the listed below as a backup just incase the ubp does not respond the next time. :)

 >   ## Backports
deb [http://ubuntu-backports.mirrormax.net/]("http://ubuntu-backports.mirrormax.net/") hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/]("http://ubuntu-backports.mirrormax.net/") hoary-extras main universe multiverse restricted

---

### Post by vanaedium on 2005-06-30
thanx works!!  :)

---

