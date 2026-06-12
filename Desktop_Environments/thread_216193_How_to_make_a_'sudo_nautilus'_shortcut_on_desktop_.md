---
title: "How to make a 'sudo nautilus' shortcut on desktop? [solved]"
date: 2006-07-15
forum: Desktop Environments
---

### Post by seshomaru samma on 2006-07-15
I would like to make an icon on the desktop that would launch a sudo-nautilus session without having to put in the password everytime it launches ,is there a way to do that?

---

### Post by Ramses de Norre on 2006-07-15
```
export EDITOR=gedit && sudo visudo
```
Add a line ```
username ALL= NOPASSWD: /usr/bin/nautilus
```
(replace username by your username)
Then make a launcher and set gksudo nautilus as command.

EDIT: you may need to run ```
xhost +
``` in order to get this working

---

### Post by seshomaru samma on 2006-07-15
Thanks
But when I create a launcher nothing happnes
If I change the type from 'application' to 'service' then it does work but I need to always choose whether to run /disply/run from terminal or whatever.

---

### Post by matthew on 2006-07-15
Right click on the desktop, select "Create Launcher..."

In the dialog box enter the following:

```
Name: Nautilus as Root (or whatever you want to call it)
Generic Name: anything you want
Comment: anything you want
Command: gksudo nautilus
Type: application
Icon: (click to select and pick one you like, maybe from /usr/share/pixmaps)
```Hit "OK"

---

### Post by seshomaru samma on 2006-07-15
Thank you .it works:-D

---

### Post by matthew on 2006-07-15
> **seshomaru samma said:**
> Thank you .it works:-DYou are very welcome.

---

### Post by dr k on 2006-08-20
This just solved a whole world of problems for me.  Thank you very much.

---

### Post by ardchoille on 2006-08-20
> **seshomaru samma said:**
> I would like to make an icon on the desktop that would launch a sudo-nautilus session without having to put in the password everytime it launches ,is there a way to do that?

It's better to use gksudo with nautilus as nautilus is a gui app. Use sudo for cli apps and gksudo for gui apps:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by ardchoille on 2006-08-20
> **matthew said:**
> Right click on the desktop, select "Create Launcher..."

In the dialog box enter the following:

```
Name: Nautilus as Root (or whatever you want to call it)
Generic Name: anything you want
Comment: anything you want
Command: gksudo nautilus
Type: application
Icon: (click to select and pick one you like, maybe from /usr/share/pixmaps)
```Hit "OK"

Very nice trick ;)

---

