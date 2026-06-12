---
title: "Desktop Dead after upgrade Xfce 4.8 (Xubuntu 10.10)"
date: 2011-03-10
forum: Desktop Environments
---

### Post by Taltos DCLXVI on 2011-03-10
Hello,
 
I installed Xubuntu 10.10, fresh i don't configure or installed another program, i only installed nvidia drivers (I have a Geforce 9600 GT video card). The entire operating system, and xfce 4.6 was working fine. 
 
After, I make an upgrade to xfce 4.8, and when i loged on, everything loaded ok: xfce 4.8 version is working fine, the panels loaded and i can add items. 
 
But there is a problem:
 
My wallpaper image doesn't appear on desktop (only brown solid color), it doesn't show icons, i can't change wallaper in configuration panel (i can add an image but it does not appear in desktop), when I plug in a pendrive usb icon does no appear. And when I right click on the deadspace on the background the right click menu does not come up. 
 
When i open desktop folder in thunar there is information, but icon files does not appear in desktop
 
I thing that maybe is a setting that i can solve typing something in terminal, but i don't know what, i searched in google and in this forum and i found only one post but not related to xfce 4.8 and it was not useful
 
[http://ubuntuforums.org/showthread.php?t=816212&highlight=xfce+desktop+dead](http://ubuntuforums.org/showthread.php?t=816212&highlight=xfce+desktop+dead)
 
 
 
Could you help me please?

---

### Post by hhh on 2011-03-10
You didn't say where you installed Xfce 4.8 from. Did you at least keep track of what packages were replaced/upgraded and which ones were removed? Then you could install/reinstall from the Maverick repo...
[http://packages.ubuntu.com/maverick/xfce4](http://packages.ubuntu.com/maverick/xfce4)

---

### Post by Taltos DCLXVI on 2011-03-10
Thanks for reply,
 
I installed following this instructions
 
sudo add-apt-repository ppa:koshi/xfce-4.8

sudo apt-get update

sudo apt-get install xubuntu-desktop

(this last instruction does not work, so i open synaptic and checked all xfce items marked as update, and apply)

---

### Post by hhh on 2011-03-10
Try the ppa-purge instructions for koshi from here...
[http://www.webupd8.org/2011/01/xfce-48-ubuntu-1004-and-1010-ppas.html](http://www.webupd8.org/2011/01/xfce-48-ubuntu-1004-and-1010-ppas.html)

---

### Post by Taltos DCLXVI on 2011-03-11
I solved this (well i think that is a walkaround :)), 
 
First i added a new user, when i loged on everything works ok.
 
Then i deleted user with problem desktop, i deleted user folder in home folder, and add new user with the same name.
 
When i loged on, new user works fine, i can change wallaper, right click works ok.
 
 
Could someone tell me if i can post thread in spanish language in this forum?
 
And second, how do i mark that this problem was solved, do i only have to write [SOLVED] in title field?
 
Thanks,

---

