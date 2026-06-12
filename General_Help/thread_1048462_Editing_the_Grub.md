---
title: "Editing the Grub"
date: 2009-01-23
forum: General Help
---

### Post by Robster2 on 2009-01-23
I have about 10 versions of Ubuntu in my grub.

I don't know how I got all these versions but I would like to reduce them to something manageable. 

Thanks for your help.

---

### Post by Kevbert on 2009-01-23
Please take a look at [COLOR="Red"][this]("http://ubuntuforums.org/showthread.php?p=6585114#post6585114")[/COLOR] post.  You've probably got a larger number of versions due to updates.  When you use Synaptic it should remove the grub entries for you and free up some boot partition space.

---

### Post by Robster2 on 2009-01-27
Thanks !

---

### Post by sumit.kalra999 on 2009-01-27
open your terminal window and edit into menu.lst in root mode by using following command
```

sudo vi /boot/grub/menu.lst

```

---

### Post by sumit.kalra999 on 2009-01-27
if you are not familiar with vi editor, use gedit to change menu.lst using following command
[code]
gksu gedit /boot/grub/menu.lst
[\code]

---

### Post by thomas228 on 2009-01-27
> **Robster2 said:**
> I have about 10 versions of Ubuntu in my grub.


I don't know how I got all these versions but I would like to reduce them to something manageable. 

Thanks for your help.

Hi

Try Startup-manager
System > Administration > Synaptic Package Manager
Search button [COLOR="Red"]startupmanager[/COLOR]
Mark for installation
Apply

This program gives a number of options for  grub and when installed can be found 
System > Administration > StartUp-Manager

Good luck

Tom

---

### Post by drs305 on 2009-01-27
Here's a tutorial for StartUp-Manager - the gui app that will edit grub's menu.lst for you:
[StartUp-Manager and Editing menu.lst]("http://ubuntuforums.org/showthread.php?t=818177")

There are also some hints if you really do want to edit it manually.

---

