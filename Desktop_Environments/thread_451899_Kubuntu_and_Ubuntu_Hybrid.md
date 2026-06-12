---
title: "Kubuntu and Ubuntu Hybrid?"
date: 2007-05-22
forum: Desktop Environments
---

### Post by rgraves22 on 2007-05-22
So, I wanted to try out KDE ( was using gnome )...

did ```
sudo apt-get install kubuntu-desktop
```

When I reboot, it comes up as kubuntu ( which is what I wanted ).. I wanted it to go back to regular ubuntu so I did the ```
 sudo apt-get install ubuntu-desktop
``` and it tells me that I have the most up to date version of ubuntu desktop.

How do I switch back to ubuntu vs kubuntu?? I'm a relativly n00b, although my knowledge of linux has grown over the last month and a half that I have been using linux.. 

7.04 btw...

---

### Post by Clay_Banger on 2007-05-22
logout, and on the screen where you type your user name and password, there will be a menu with various sessions that you can use, two of them will be "KDE" and "Gnome" just select the one you want and proceed to logon.

---

### Post by rgraves22 on 2007-05-22
Right, but when I reboot, it still says " Kubuntu " on it.. I want to run ubuntu

---

### Post by Soybean on 2007-05-22
> **rgraves22 said:**
> Right, but when I reboot, it still says " Kubuntu " on it.. I want to run ubuntu

All the Gnome software (the "Ubuntu stuff") is still there; the kde install process just set the KDE things  to be the default.

The main one you're noticing is that it's using kdm instead of gdm to handle your login. To change that back, I believe you just have to edit /etc/X11/default-display-manager and change whatever it says now to:
```
/usr/sbin/gdm
```

---

### Post by geek2330 on 2007-05-22
Just as mentioned, right on the login screen on the left of the login fields there'll be a little notepad icon, if you click it you will see the options.
If you don't see that then check on the lower bottom for an "Options" option.

---

### Post by rgraves22 on 2007-05-23
> **Soybean said:**
> All the Gnome software (the "Ubuntu stuff") is still there; the kde install process just set the KDE things  to be the default.

The main one you're noticing is that it's using kdm instead of gdm to handle your login. To change that back, I believe you just have to edit /etc/X11/default-display-manager and change whatever it says now to:
```
/usr/sbin/gdm
```


I changed it to GDM on the /etc/X11/default-display-manager, rebooted and it still displays kubuntu on startup..

EDIT: Kubuntu loads ( the bar goes across the screen ) than it goes into the terminal.. 

Not sure what to do from here....

---

### Post by rgraves22 on 2007-05-23
Figured it out... 

needed /usr/sbin/gdm instead of /usr/bin/gdm

Thanks anyway!!

---

### Post by IanW on 2007-05-23
> EDIT: Kubuntu loads ( the bar goes across the screen ) than it goes into the terminal.. 

The "Kubuntu" you see displayed is just the splash screen. It makes no difference to which version loads.
When you installed kubuntu-desktop, Grub merely got pointed to the Kubuntu splash instead of the Ubuntu one.

It is safe to ignore it.

 Just select Gnome or KDE for your user session at the login screen as instructed by Clay_Banger and Geek2330.

---

### Post by Ptero-4 on 2007-05-23
> **rgraves22 said:**
> I changed it to GDM on the /etc/X11/default-display-manager, rebooted and it still displays kubuntu on startup..

EDIT: Kubuntu loads ( the bar goes across the screen ) than it goes into the terminal.. 

Not sure what to do from here....

What you see is the kubuntu usplash. there's an article in the document storage facility that shows how to restore the ubuntu usplash.

---

