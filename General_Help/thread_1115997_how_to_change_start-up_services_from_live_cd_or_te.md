---
title: "how to change start-up services from live cd or terminal"
date: 2009-04-04
forum: General Help
---

### Post by sharkbite1414 on 2009-04-04
How do i change start-up services from live cd or terminal as i mucked it up and want to change it back but my ubuntu 8.10 ony starts a terminal. I don't know very many terminal commands and i am working from a live cd at the moment.

---

### Post by Peter09 on 2009-04-04
As a beginning to this - try typing

```
startx
```

from a terminal - tell us what happens.

---

### Post by sharkbite1414 on 2009-04-04
ok i've got my nice graphics back but when i when System > Administration > Services i found i couldn't unlock it!!!:(

---

### Post by Peter09 on 2009-04-04
Services will not help, I suspect that you are booting into terminal mode because your session is now defined at that level - do you get the login prompt? If so look in the sessions menu and make sure that a Gnome session is selected.

---

### Post by sharkbite1414 on 2009-04-04
I know what to enable in services to get it to work (the one named Graphical login manager (kdm)) I recently had kubuntu installed but i un-installed it. Out of interest i went to see if i could change the login window but it said 

GDM (GNOME Display Manager) is not running.

You might be using a different display manager, such as KDM (KDE Display Manager), CDE login (dtlogin), or xdm.  If you wish to use this feature, then your system will need to be configured to use GDM instead.

How do i get it to use GDM instead?

---

### Post by sharkbite1414 on 2009-04-05
Yay! I've got my graphical logins back! However it's using the kde login manager, how to i get it to use the the gnome login manager so i can safely disable the kde login manager?

Thanks for all the help so far!!!:)

---

### Post by Peter09 on 2009-04-05
Mmm... not to sure but try 

System->Admin->Login Window

---

### Post by sharkbite1414 on 2009-04-05
Tried that but it said:

GDM (GNOME Display Manager) is not running.

You might be using a different display manager, such as KDM (KDE Display Manager), CDE login (dtlogin), or xdm.  If you wish to use this feature, then your system will need to be configured to use GDM instead.

I know i'm using KDM but i don't know how to configure my system to use GDM.

---

### Post by Peter09 on 2009-04-05
Try

[http://www.howtogeek.com/howto/ubuntu/how-to-switch-between-gdm-and-kdm-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/how-to-switch-between-gdm-and-kdm-on-ubuntu/)

---

### Post by sharkbite1414 on 2009-04-05
Thank you.

It's all working now.:)

---

