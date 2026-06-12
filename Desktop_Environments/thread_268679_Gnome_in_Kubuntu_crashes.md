---
title: "Gnome in Kubuntu crashes"
date: 2006-09-30
forum: Desktop Environments
---

### Post by Dirty Ole on 2006-09-30
Hello,

I installed Kubuntu Dapper Drake few days ago and wanted to try Gnome so I did this

```
sudo aptitude install ubuntu-desktop
```

Then I rebooted and got into gnome. Then I tried to install a new theme 'Candido' so I downloaded the GTK 2+ engine and then a theme file. I applied it and just when I did that I got error messages saying - applets(like trash volume could not be loaded delete or dont delete from panel). Note that KDE is working normally.

Next time onwards when I logged into gnome either of the following happened:

1. the panel and tasklist appeared without the applets and with those error messages. When I started any application its window appeared and then disppeared without fully loading(ie no text in the window showed up). this happened for all programs except nautilus.

2. the two panels(blank) and black desktop background flash and seem to go in a loop.

I then executed this command 

```
sudo aptitude purge ubuntu-desktop
```

rebooted then again

```
sudo aptitude install ubuntu-desktop
```

But the problem did not go away .Please help. 

(KDE is working normally)

---

### Post by devils_casper on 2006-09-30
Hi !

which is your default Desktop Manager?
you should use KDM.

sudo dpkg-reconfigure kdm

select kdm from given option.



casper

---

### Post by Dirty Ole on 2006-09-30
> **devils_casper said:**
> Hi !

which is your default Desktop Manager?
you should use KDM.

sudo dpkg-reconfigure kdm

select kdm from given option.



casper

It is KDM. This happens when I select the session to be Gnome.

---

### Post by devils_casper on 2006-09-30
okk... 
i also installed ubuntu-desktop and had same problem. during ubuntu-desktop install, it asked for default desktop manager. i selected 'gdm' and got problems like you have right now. i changed default desktop manager to kdm through dpkg-reconfigure and stopped 'gdm' at 'boot up' in kcontrol ---> system administration ---> system services.
its working fine now......



casper

---

### Post by Dirty Ole on 2006-09-30
Thanks but that didn't fix it. 

I tried removing the theme engine but in vain.

---

### Post by chavo on 2006-09-30
The problem is the gtk-qt engine. It writes a file in your home directory called .gtkrc-2.0 and then adds a couple of lines to your ~/.bashrc to make gtk apps read this file when your running KDE. This file conflicts with gnome when you login, as you can see. A workaround is to remove or rename this file, either when you log out of KDE or before you log into Gnome.

---

### Post by Dirty Ole on 2006-09-30
Thank you chavo very much. That *was* the problem.:D

---

