---
title: "Virtual Desktop problem in Kubuntu with compiz/xgl install"
date: 2006-09-02
forum: Desktop Environments
---

### Post by cdr377 on 2006-09-02
Hi, I've installed but Ubuntu and Kubuntu on my pc. I then preceded to install the nvidia drivers and then the compiz xgl stuff. I followed the Ubuntu Guide for installing xgl on Ubuntu. Then I searched high and low for the slightest hint for installing it on Kubuntu. Finally I found some help. Everything seems to work just fine I get the cool effects for windows and menus but Virtual Desktop for Kubuntu doesn't work anymore. It works just fine in Ubuntu but after setting up compiz/xgl for kubuntu there is no more virtual desktop. Even if I go to System Settings -> Desktop and enable multiple desktops setting it to 4 it always defaults back to 1, so I can never do the cool cube thing with kubuntu like I can with ubuntu. Any clues about this? I can't find any help on the net even afer searching these very forums for a while. Any help would be greatly appreciated! Thanks!

---

### Post by elubuntero2008 on 2008-05-26
Hello, It happened the same to me. I've installed kubuntu 8.0 and compiz-fusion and I couldn't change the number of virtual desktops. 
So I've found out that in kde, the program kcmshell is the one that is changing that configuration.
I excecuted 
$ sudo kcmshell desktop
($ is the prompt)
desktop is the module.
It seems that the program didn't have the necessary permissions. 

Bye Bye.

---

### Post by elubuntero2008 on 2008-05-31
Hello again. I was looking for that solution and I found that the number of virtual desktops is 1.
You only have to change the Horizontal Virtual Size in CompizConfig Settings Manager (Desktop Size Tab).

Thanks.

---

