---
title: "KDE installed, now how do I uninstal GNOME?"
date: 2009-03-18
forum: Desktop Environments
---

### Post by GeistDev on 2009-03-18
Hey everyone,

I am semi-new to Ubuntu and learning as I go on with it.  I installed KDE4 a week or so ago and love it, and now I want to get rid of GNOME.  

My first question is, how do I set the KDE login to be the default login, as the GNOME 'human' log in still displays when my computer is turned on.

My second question is, after I have the KDE login as the default, how can I go about removing GNOME completely?


Thanks for all your help!

---

### Post by metallicamike on 2009-03-18
you could just do a fresh install of kubuntu...

---

### Post by GeistDev on 2009-03-18
Uh, yes, I could, except I am not starting from scratch -so that is NOT an option.  Now I have KDE and GNOME both, I just want to get rid of GNOME, simple.

---

### Post by Name change on 2009-03-18
> **GeistDev said:**
> Hey everyone,

I am semi-new to Ubuntu and learning as I go on with it.  I installed KDE4 a week or so ago and love it, and now I want to get rid of GNOME.  

My first question is, how do I set the KDE login to be the default login, as the GNOME 'human' log in still displays when my computer is turned on.

My second question is, after I have the KDE login as the default, how can I go about removing GNOME completely?


Thanks for all your help!
You have to change your log in screen from GDM to KDM. Don't know how, sorry. That was one of reasons why I decided to switch to Arch, because even when I was still using Kubuntu I knew how to do that on Arch but not on Kubuntu. But my guess would be that you have to change something in /etc/rc.d

Now how to uninstall Gnome:
```
sudo apt-get remove ubuntu-desktop
``` that should do the trick.
And there you go you have a KDE only Ubuntu :D!
Welcome to the wonderful world of KDE!

---

### Post by metallicamike on 2009-03-18
go into adept manager and uninslall gnome. But i cant guarrantee that all of your apps will stay. i suggest just keeping it the way it is now. GNOME is very usefull for some things and KDE too.they both have their strengths and weaknesses. unless of course you don't have enough HDD space.

---

### Post by GeistDev on 2009-03-18
> go into adept manager and uninslall gnome. But i cant guarrantee that all of your apps will stay. i suggest just keeping it the way it is now. GNOME is very usefull for some things and KDE too.they both have their strengths and weaknesses. unless of course you don't have enough HDD space.

I thought about keeping GNOME, but the cluttered menus are driving me crazy!


> You have to change your log in screen from GDM to KDM. Don't know how, sorry. That was one of reasons why I decided to switch to Arch, because even when I was still using Kubuntu I knew how to do that on Arch but not on Kubuntu. But my guess would be that you have to change something in /etc/rc.d

I figured it out! 

$ sudo dpkg-reconfigure gdm


Thanks for the help, everyone!

---

### Post by albinootje on 2009-03-18
> **GeistDev said:**
>  My first question is, how do I set the KDE login to be the default login, as the GNOME 'human' log in still displays when my computer is turned on.

Edit /etc/X11/default-display-manager to use kdm instead of gdm
(/usr/bin/kdm vs. /usr/sbin/gdm)
> 
My second question is, after I have the KDE login as the default, how can I go about removing GNOME completely?

If you're using 8.10, then see here :
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

And removing the meta-package ubuntu-desktop is not enough :)

---

### Post by Name change on 2009-03-18
> **albinootje said:**
> 
And removing the meta-package ubuntu-desktop is not enough :)
I always thought it was :D
My apologies to OP for my mis-information.

---

