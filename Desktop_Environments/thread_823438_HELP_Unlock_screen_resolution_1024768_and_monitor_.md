---
title: "HELP Unlock screen resolution 1024*768 and monitor choice - where?"
date: 2008-06-09
forum: Desktop Environments
---

### Post by oleksus on 2008-06-09
Hi!

Just installed xubuntu 8.04 after using Feisty for 2 years on a laptop, always in native 1024*768.

But now...

My screen goes 800*600 and I can't select monitor type anywhere!
What am I to do?

Configging some files? Which?

Help, please!

---

### Post by sammi.jo on 2008-06-09
Try this thread. Somebody had a similar problem and they seem to have had it solved by my answer there :)

[http://ubuntuforums.org/showthread.php?t=822993](http://ubuntuforums.org/showthread.php?t=822993)

---

### Post by philinux on 2008-06-09
Xorg in Hardy cannot be reconfigured now, the devs took that feature away.

There is xfix from recovery mode. And system>Prefs>Screen res

Make sure you have your graphics driver installed from system/admin hardware drivers.

---

### Post by sammi.jo on 2008-06-09
> **philinux said:**
> Xorg in Hardy cannot be reconfigured now, the devs took that feature away.

There is xfix from recovery mode. And system>Prefs>Screen res

Make sure you have your graphics driver installed from system/admin hardware drivers.

EH? I did it just yesterday!

---

### Post by philinux on 2008-06-09
You may have upgraded. A clean install is so different

sudo dpkg-reconfigure xserver-xorg 

Check the posts this does not work in hardy

---

### Post by oleksus on 2008-06-10
No upgrade, I did a clean install.

I wonder if there's a RIGHT way to edit xorg.conf file, where all the necessary lines should obviously be put.

Ugh, with that Hardy release Ubuntu seems to have gone totally user-paranoid, for the sake of foolproof stability. 
I'd say, in this case the devs should at least give the users SOME ability to alter the deeper settings. 
The way they done with Hardy is soooooo... microsoft.

---

### Post by oleksus on 2008-06-11
> **philinux said:**
> 
Make sure you have your graphics driver installed from system/admin hardware drivers.

I have *xserver-xorg-driver-trident* package installed, but in the 'system..drivers' panel the driver list is emtpy!

How do I configure it manually?

---

