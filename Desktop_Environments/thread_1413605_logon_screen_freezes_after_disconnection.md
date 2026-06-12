---
title: "logon screen freezes after disconnection"
date: 2010-02-22
forum: Desktop Environments
---

### Post by jy_moustache on 2010-02-22
Hi all

I've been getting a new issue recently. When I want to switch users, I disconnect and go to the login screen but then the login screen freezes every time.

I'm running Ubuntu Karmic Koala 9.10 and using xfce. Before xfce, I used gnome so the login screen is the one from gnome. Recently a program asked for kdialog so I had to install KDE (kubuntu-desktop package it was) and it changed the login screen but then I didn't like the new KDE login screen and wanted to switch back to the gnome one. 

I've searched the internet and the only way of doing this I found was by completely removing all KDE packages. So I did and returned to xfce with a gnome login screen, a solution with which I've been very happy before. Since then I've been having this freezes on disconnection. I regularly need to switch users because I use musical software which needs low latency and high performances. So now I have to restart the computer every time which is quite .... frustrating ! :)

The gnome package is not installed but gdm and xfce are.

I'm adding the content of /var/log/Xorg.2.log which seems to give a lead 
```
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
(EE) NVIDIA:     system's kernel log for additional error messages.
(II) UnloadModule: "nvidia"
(II) Unloading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.

```I've been searching through the web but I didn't find anything that really matched my problem...

Does anyone have an idea of how to make the login screen work again after disconnection ?

Thanks

jy

---

### Post by Jay Christnach on 2010-02-22
I have no answer to your problem with the gui logon since I'm new to Ubuntu (still about to get it working on my hardware). You wrote that you need to switch users to get low latency. So you log in as root for this? I would suggest you set the setuid attribute for the programs which have to run as root instead of logging in as root. See the man page for the chmod command for this. Running things under the root user is considered unsecure but it is still better than logging in as root altogether, because you and all the programs you run are then allowed to do anything. Also you won't need to log off and on anymore.
Tell me if I'm wrong with this, I'm still willing to learn.

---

### Post by jy_moustache on 2010-02-23
Hi

Thanks for the reply.

Actually the problem is solved. I've been playing with opening and closing sessions with gnome and xfce alternatively and restarting the computer. I works fine now.

About the latency user, I've set up a group with special real-time privileges and then I subscribed to this group. It's better than running anything as root :D

Thanks for the (intended) help anyway !! :D

jy

---

