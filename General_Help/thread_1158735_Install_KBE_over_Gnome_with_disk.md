---
title: "Install KBE over Gnome with disk?"
date: 2009-05-14
forum: General Help
---

### Post by sideffects on 2009-05-14
I currently have Ubuntu installed. I have a cap on my internet connection at my house, so I torrented the Kubuntu iso at my uncles house. I was hoping to install Kubuntu-desktop with the disc I have. Is this possible?

---

### Post by KhurramM on 2009-05-14
Better install

kubuntu

and all the other required dependencies.

If these packages can be loaded from the CD then go ahead.

But the current livecd format will not allow u to do this, maybe dvd or alternate CD will allow u. But confirm this. Since I dont have them, I cant say anything about this.

---

### Post by sideffects on 2009-05-14
how would I go about doing that from the CD though?

---

### Post by KhurramM on 2009-05-14
Insert Cd of k in g

If it auto loads to install, go ahead.

If not, goto:

System > Admin. > Software Sources > Select Cd

System > Admin. > Synaptic

If it works ok, else u need to download packages separately for kubuntu

OR use the alternateCd or DVD.

GoodLuck!!!!!!

---

### Post by sideffects on 2009-05-14
Okay thanks! I will give this a try.

---

### Post by sideffects on 2009-05-14
> **KhurramM said:**
> Insert Cd of k in g

If it auto loads to install, go ahead.

If not, goto:

System > Admin. > Software Sources > Select Cd

System > Admin. > Synaptic

If it works ok, else u need to download packages separately for kubuntu

OR use the alternateCd or DVD.

GoodLuck!!!!!!

I couldn't get it to work. Does it matter if I use a DVD or a CD, because all I have around are DVD-Rs.

---

### Post by bodhi.zazen on 2009-05-14
You need to use the (Kubuntu) alternate CD (the desktop CD does not have the packages).

---

### Post by sideffects on 2009-05-17
Thanks I got it to work! However, even though I still use GNOME as my default the boot screen is Kubuntu instead of Ubuntu. Any way to change that back?

---

### Post by bodhi.zazen on 2009-05-17
use :
```
sudo dpkg-reconfigure gdm
```

you will get a dialog box allowing you to select gdm or kdm

---

### Post by sideffects on 2009-05-17
It still let's me use gnome as my default. Basically what happens is it boots up, but it shows the Kubuntu logo, and then it boots into Gnome. Not really a hinderance, just a small annoyance.

---

### Post by bodhi.zazen on 2009-05-17
are you using auto-login ?

---

### Post by sideffects on 2009-05-17
no, I have a login screen with two users listed.

---

### Post by bodhi.zazen on 2009-05-17
You set your default session at the log in screen, check the menu ;)

---

### Post by sideffects on 2009-05-18
My default is gnome. What happens is I boot up and it shows the Kubuntu boot screen, but then I login as my user and it loads GNOME.

---

### Post by bodhi.zazen on 2009-05-18
What do you want it to do ? use GDM ? log into kde ?

to change to gdm, use sudo dpkg-reconfigure gdm

to set you default to KDE, on the KDM (log in screen) go to the sessions menu and set the default to KDE (instead og gnome).

---

### Post by sideffects on 2009-05-18
I just want the boot screen to show Ubuntu instead of Kubuntu, that's all.

---

### Post by JK3mp on 2009-05-18
Then you want GDM. Just use GDM but set your session to use KDE as you DM.
At GDM login should click options sessions...KDE.

---

### Post by sideffects on 2009-05-18
Last try then I give up explaining it, I guess I can't explain it well enough. Sorry. I am using Gnome, I like Gnome, and Gnome is set as my default. The only problem is the boot screen (The image with the loading bar and the background is black) ever since I successfully installed KDE the boot screen is the blue Kubuntu one and I was just wondering if there is a way to change the boot screen back to the yellow Ubuntu one.

---

### Post by bodhi.zazen on 2009-05-18
> **sideffects said:**
> Last try then I give up explaining it, I guess I can't explain it well enough. Sorry. I am using Gnome, I like Gnome, and Gnome is set as my default. The only problem is the boot screen (The image with the loading bar and the background is black) ever since I successfully installed KDE the boot screen is the blue Kubuntu one and I was just wondering if there is a way to change the boot screen back to the yellow Ubuntu one.

Ah, now I think I understand, you want to change what is called the boot splash, the image displayed while ubuntu is booting, before GDM/KDM ;)

Easiest was is via startupmanager

Here ia  brife overview : 

[http://www.downloadsquad.com/2008/10/10/ubuntu-tip-use-startup-manager-to-edit-your-boot-menu/](http://www.downloadsquad.com/2008/10/10/ubuntu-tip-use-startup-manager-to-edit-your-boot-menu/)

---

### Post by sideffects on 2009-05-18
thanks a ton :). Sorry for the confusion. I will try this out when I get off of work.

---

### Post by JK3mp on 2009-05-19
> **sideffects said:**
> thanks a ton :). Sorry for the confusion. I will try this out when I get off of work.

Ahh...now i understand what you meant. Hope bodhi's link got u figured out.

---

### Post by sideffects on 2009-05-19
Thanks bhodi, seemed to work!

---

