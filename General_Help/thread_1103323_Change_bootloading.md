---
title: "Change bootloading"
date: 2009-03-22
forum: General Help
---

### Post by pheonixdragon on 2009-03-22
Hi,

I installed Ubuntu and Suse Linux on an existing Vista laptop.

It always boot up Ubuntu or Suse Linux first.

How do I change the first boot to Vista?:popcorn:

---

### Post by drs305 on 2009-03-22
Are you using grub? If so, you can manually edit grub's menu.lst to make vista start first. You can also install StartUp-Manager, a gui app that edits menu.lst for you.

Install it with:
```
sudo apt-get install startupmanager
```
Run it via System, Administration, StartUp-Manager.
You can set the default operating system in the boot options tab.

You can access a guide on using startupmanager and editing menu.lst via the link in my signature line.

---

### Post by pheonixdragon on 2009-03-22
> **drs305 said:**
> Are you using grub? If so, you can manually edit grub's menu.lst to make vista start first. You can also install StartUp-Manager, a gui app that edits menu.lst for you.

Install it with:
```
sudo apt-get install startupmanager
```
Run it via System, Administration, StartUp-Manager.
You can set the default operating system in the boot options tab.

You can access a guide on using startupmanager and editing menu.lst via the link in my signature line.


Tried to install startup manager................what have I done wrong?

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package startupmanager

---

### Post by drs305 on 2009-03-22
> **pheonixdragon said:**
> How come I don't see the startupmanager in System-->Administration?

If you installed startupmanager that is where the menu normally puts it (System, Administration, StartUp-Manager). You can also run it from the command line with:
```
gksudo startupmanager
```

---

### Post by pheonixdragon on 2009-03-23
> **drs305 said:**
> If you installed startupmanager that is where the menu normally puts it (System, Administration, StartUp-Manager). You can also run it from the command line with:
```
gksudo startupmanager
```

I tried it but nothing happened neither can I see the startupmanager.

---

### Post by cariboo on 2009-03-23
MAke sure you have all the repositories enabled in System-->Administration-->Software Sources, then use Synaptic Package Manager to install startupmenager.

Jim

---

### Post by pheonixdragon on 2009-03-26
> **cariboo907 said:**
> MAke sure you have all the repositories enabled in System-->Administration-->Software Sources, then use Synaptic Package Manager to install startupmenager.

Jim

Thanks to all who replied, it working now.:popcorn:

---

