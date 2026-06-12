---
title: "Kubuntu 11.04 Deiconify windows"
date: 2011-05-05
forum: Desktop Environments
---

### Post by kalafox on 2011-05-05
Hello

I' ve been using Ubuntu for more than one year now, both with Gnome and KDE.

Recently I updated to  V 11.04 Natty Narwhal. 
Under** Kubuntu,** when I iconify a window I cannot find a way to restore it from the** taskbar**.

Of course I can use ALT+TAB to navigate through the open applications.

But I was used to the iconify / deiconify method.

---

### Post by ankspo71 on 2011-05-05
Hi,
Are you saying that when you click on a minimized window button in your panel it does not restore the window? If so then this might be a bug, or a problem with a kde configuration file... probably the one located at /home/yourname/.kde/share/config/plasma-desktop-appletsrc. Try renaming this configuration file to plasma-desktop-appletsrc-backup, then log out then log back in again, and then check to see if the problem is gone. 

"plasma-widget-smooth-tasks" and "plasma-widget-fancytasks" are good alternatives to the "Task Manager" (window list) applet in the panel.

Hope this helps.

---

### Post by kalafox on 2011-05-06
> **ankspo71 said:**
> Hi,
Are you saying that when you click on a minimized window button in your panel it does not restore the window? If so then this might be a bug, or a problem with a kde configuration file... probably the one located at /home/yourname/.kde/share/config/plasma-desktop-appletsrc. Try renaming this configuration file to plasma-desktop-appletsrc-backup, then log out then log back in again, and then check to see if the problem is gone. 

"plasma-widget-smooth-tasks" and "plasma-widget-fancytasks" are good alternatives to the "Task Manager" (window list) applet in the panel.

Hope this helps.

No, What I'm saying is that when I click on an minimize (or iconify) button. The window "disapear" completly., i.e. I dont find any button or icon to restore it .

Basically, most graphics environments allows you to minize and later restore a window. My problem is that I can do the minimize operation. but I don't find any widget to restore the window. 
Before when I minimized a window, it was iconified in the taskbar, and by clicking on that icon, I used to restore the window. It still works well with Classic Ubuntu, but with the KDE desktop I don't fin where the minimized windows are stored.

Also the aeropeek preview over the desktops icons in the taskbar doesn't works anymore.

---

### Post by kalafox on 2011-05-16
I completely reinstalled Kubuntu 11.04 from the live CD, and now everything run fine.
When I minimize a window it does appear properly in the taskbar.
May be it was a conflict with Compiz?

---

### Post by wildmanne39 on 2011-05-16
> **kalafox said:**
> I completely reinstalled Kubuntu 11.04 from the live CD, and now everything run fine.
When I minimize a window it does appear properly in the taskbar.
May be it was a conflict with Compiz?
Hi,you can not enable any effect in compiz when running unity, if you want compiz you need to log out and hit your user name and go to the bottom of the screen and click ubuntu classic and you can enable effects, I am running the cube and full effects in classic mode no problem at all.:D

---

### Post by Copper Bezel on 2011-05-16
The KDE configuration bit is more likely. There's nothing you can do in Compiz to cause windows to unmap instead of iconifying, so far as I know, and even then, they wouldn't appear in Compiz's Alt+Tab switcher.

Wildmanne39, please read the questions before answering.

---

