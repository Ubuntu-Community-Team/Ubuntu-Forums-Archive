---
title: "Debian Multi-Boot Question"
date: 2007-02-17
forum: Debian
---

### Post by foxmulder881 on 2007-02-17
I have never actually used Debian before and I am actually disgraced at myself for it. After all, it does provide the foundations for Ubuntu. So I have taken it upon myself to try it out.

My question is, I already have a dual-boot system installed with Ubuntu and Windows XP (for gaming) booting via GRUB. When I install Debian on the same system, will it create a new GRUB configuration file automatically, giving me the option to boot either Ubuntu, Debian or Windows? Or is there something I should do manually? Or should I not even attempt it?

Thanks in advance.

---

### Post by unisol on 2007-02-17
yes grub will be updated and you will have a triple-boot system. you can even use the same swap file for both debian and ubuntu.

---

### Post by foxmulder881 on 2007-02-17
Cool thanks for the reply. I'm just about to give it a shot. Fingers crossed.

---

### Post by foxmulder881 on 2007-02-17
Alright, I have installed Debian with GRUB successfully picking up all current OSs.

My question now is, how the hell do you login to the Debian GUI? All I can do is login to a command line system. Where's the GUI? Or does Debian have none?

---

### Post by neoflight on 2007-02-18
> **foxmulder881 said:**
> Alright, I have installed Debian with GRUB successfully picking up all current OSs.

My question now is, how the hell do you login to the Debian GUI? All I can do is login to a command line system. Where's the GUI? Or does Debian have none?

after you login as a user...you login as root 

```
su
```

then install gdm/xdm/kdm which ever you prefer
```
aptitude install gdm
``` 
then you will get the login screen.. if it complaints about xserver stuff then install xserver-xorg too...

---

### Post by foxmulder881 on 2007-02-18
I have given up on Debian now.

I have removed the partition and forgot that it also removes the GRUB configuration. I have reinstalled Ubuntu again on a separate partition. So my current setup looks like this:

hda1 Windows XP
hdb1 Ubuntu (Preferred install)
hdb2 Ubuntu (New install)

As you see, I actually now have 2 Ubuntu installations on the one drive, hdb. GRUB is installed on hda1 and would be pointing to the hdb2 installation, I think. I want GRUB to point to the hdb1 installation so that I can remove my newly created and unnecessary second Ubuntu install.

How do I change to where GRUB points to? Possible? :confused:

---

### Post by foxmulder881 on 2007-02-21
Problem solved.

---

