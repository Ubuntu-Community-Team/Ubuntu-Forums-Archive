---
title: "ubuntu with xubuntu desktop"
date: 2012-07-30
forum: Desktop Environments
---

### Post by DouglasAdams on 2012-07-30
when i tried the live ubuntu 12.04 i had problems. the menu showed an empty box which looked like someone was shining a bright blue light at the back of it. very pretty but totally useless. i guess it was the videos drivers. 
i was short of time so i installed xubuntu 12.04 instead. then i found i didn't like it's apps. so i've spent ages replacing them with one's i like, i.e. mostly the one's that are standard with ubuntu.
is there a simple, i.e. no CLI, way to install ubuntu BUT with the xfce desktop as the default (only if possible) desktop please?

p.s.
a box was shown, while ubuntu was loading, which i guess would have been to select desktops but it only showed one row of char's (one option prob), in fact it only showed the top part of the chars, and it disappeared almost instantly.

---

### Post by tartalo on 2012-07-30
[http://www.psychocats.net/ubuntu/xfce](http://www.psychocats.net/ubuntu/xfce)

---

### Post by Rodney9 on 2012-07-31
Xubuntu Help, Guide and Review


[http://xubuntu.org/news/faq-1204-precise/](http://xubuntu.org/news/faq-1204-precise/)

[http://www.dedoimedo.com/computers/xubuntu-pangolin.html](http://www.dedoimedo.com/computers/xubuntu-pangolin.html)

[https://plus.google.com/u/1/112064450121097287690/posts](https://plus.google.com/u/1/112064450121097287690/posts)

[http://sites.google.com/site/easylinuxtipsproject/xubuntu](http://sites.google.com/site/easylinuxtipsproject/xubuntu)

[http://wiki.xfce.org/recommendedapps](http://wiki.xfce.org/recommendedapps)

Rodney

---

### Post by DouglasAdams on 2012-07-31
sorry but i already know how to add xfce to ubuntu and switch to it.
and i know which packages are included in xubuntu - they are what i do NOT want!
i want ubuntu but with the xfce frontend.
however,
i can't install ubuntu to simply add & switch to it after an install.
is it possible to install, without using cli, ubuntu but with the xfce desktop as an option please?

---

### Post by vasa1 on 2012-07-31
I think people are having difficulty understanding what your problem is.

---

### Post by DouglasAdams on 2012-07-31
i don't seem to be able to install ubuntu 12.04 due to, what look to me like, a vidoe driver issue.
however, i want everything that comes with ubuntu (all the apps) - except it's desktops.

is there a simple way, i.e. without using a mass of cli, to install ubuntu BUT with the xfce desktop as it's default (or only) please?

---

### Post by westie457 on 2012-07-31
Hi, one possible way is to start with a minimal xfce install. Take a look here to get started. [http://disambiguation.wordpress.com/2008/08/17/a-minimal-ubuntu-install-the-basics/](http://disambiguation.wordpress.com/2008/08/17/a-minimal-ubuntu-install-the-basics/)

After you have done the above you can install synaptic package manager and use that to install the ubuntu packages you want.

---

### Post by cottfcfan on 2012-07-31
If I understand what you're asking for, then just install xubuntu 12.04 instead of ubuntu, then using synaptic or software centre, just install all the ubuntu apps you want, and at the same time uninstall the xfce apps that you do not require.

---

### Post by cortman on 2012-07-31
All you want is the XFCE DE?

```
sudo apt-get install xfce4
```

---

### Post by DouglasAdams on 2012-07-31
sorry guys but i don't think you see what i'm after.

> **cortman said:**
> All you want is the XFCE DE?
```
sudo apt-get install xfce4
```
cheers, but i know how to install xfce.
problem is, i can't install unbuntu to get to the point where i could do as you suggest.


> **cottfcfan said:**
> If I understand what you're asking for, then just install xubuntu 12.04 instead of ubuntu, then using synaptic or software centre, just install all the ubuntu apps you want, and at the same time uninstall the xfce apps that you do not require.
this is exactly what i did ... and it took forever.
especially as synaptic would only let me enter a 3 or 4 apps at once, after that it seemed to stop finding things (apps).


> **westie457 said:**
> Hi, one possible way is to start with a minimal xfce install. Take a look here to get started. [http://disambiguation.wordpress.com/2008/08/17/a-minimal-ubuntu-install-the-basics/](http://disambiguation.wordpress.com/2008/08/17/a-minimal-ubuntu-install-the-basics/)
After you have done the above you can install synaptic package manager and use that to install the ubuntu packages you want.
this sounds like the best option up to now.
is there a list of the ubuntu apps that i can pull into synaptic?
... i know, i'm damn lazy.

---

### Post by cottfcfan on 2012-07-31
Douglas..
I can't understand why Xubuntu would install but not Ubuntu.
Basically they are exactly the same, but with different apps added & a different window environment.
Should not stop it installing.
Maybe check your download is sound and that the burn is good.

---

### Post by DouglasAdams on 2012-07-31
disks checked, checksums, etc all fine.
actually it DID install.
however, after the install i could not do anything as all the menus were blank with a lighting effect around the menu frame.
thought ...
is there a key-stroke to shutdown the de?
i was thinking that if i closed the [faulty] menu.
then i could use cli to install & run xfce4 ...
might that work??

---

### Post by tartalo on 2012-07-31
> **DouglasAdams said:**
> is there a key-stroke to shutdown the de?

ctrl + alt + F1 should open a text terminal for you. 

From F1 to F6 they are all text terminals, F7 is the graphic enviroment.

---

PS: Ctrl + Alt + Backspace used to kill the X server, that is not the case anymore but there's an alternative (scroll to the bottom): [https://wiki.ubuntu.com/XorgCtrlAltBackspace/](https://wiki.ubuntu.com/XorgCtrlAltBackspace/)

---

### Post by The Cog on 2012-07-31
As tartalo says, you could install Ubuntu and then drop to a text console using Ctrl+Alt+F1 and then "sudo apt-get install xfce". Then Ctrl-Alt-Del to reboot. The login page should then offer you a choice of desktop environment.

Or if you refuse to type those four words into a text console, you could install xfce and then use synaptic to install ubuntu-desktop, which again should get you a choice of DE at the login prompt.

---

### Post by DouglasAdams on 2012-08-01
i think tartalo's cure sounds the best and by far the least painful cure.  :)
that's certainly the direction i'm going to head.
many thanks for everyone's contributions.

---

