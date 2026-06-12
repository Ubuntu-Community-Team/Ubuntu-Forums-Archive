---
title: "gnome-pannel dosn't appear"
date: 2011-09-13
forum: Desktop Environments
---

### Post by Siva Sankaran on 2011-09-13
I upgraded Ubuntu from 10.10 to 11.04 . the system said upgrade is complete but with some errors(**it says gconf is failed to install or update**). when I log in after upgrade desktop is shown without  panel then i launch terminal Using launcher(right click on desktop and on clicking create launcher menu in that pop up.on the command field of the create launcher window i typed gnome-terminal) and then only I can open terminal. And on terminal i run the command  gnome-panel.  I have to do this on every login.  
 Is there any start program list ?

I read that Ubuntu 11.04 natty has unity desktop environment. But i  still have gnome2 . there is libre office instead of open office in my system

There was an error in the middle of upgrading process it is:
   ...............   . . . . . . . cannot open pixbuf loader module file /lib/gdk-pixbuf 2.0/2. . . 

how to make Ubuntu show pannels default after login.

---

### Post by Siva Sankaran on 2011-09-13
On typing pixbuf  in Quick filter field in Synaptic packet manager  I got some packages list. In the list I found "**libgdk-pixbuf2.0-dev**" ( describtion tells "This package contains the header files which are needed for using GDK Pixbuf.")  which is not installed . So I install and restart the system I fix it.

screenshot is attached here


I entered command to find which desktop environment is there in system(whether gnome or unity)


               ```
  $echo $DESKTOP_SESSION  
                              gnome
```
It told that gnome.
what happened here ?

---

### Post by raja.genupula on 2011-09-13
in ubuntu unity you dont have gnome-panel. for that you need to move to ubuntu classic . if you wanna see it 

logout first and then in the login screen you are going to have something like ubuntu classic,select it and then login . 

i think this is what you what ?

let me know

---

### Post by Siva Sankaran on 2011-09-13
I think my system has gnome desktop environment not Unity. Because system monitor tells gnome 2.32.1. And also environmental variable  $DESKTOP_SESSION has "gnome"  only. 

  After kernel begin execution it starts some other processes. Among this gnome-panel is one.

 Before installing "" package the launcher(look like in windows 7) and searching ability was not there.

 after installation and a reboot  the desktop seen with a bar(or panell) on top (with power button,time,etc..,)

My guess is gconf  was broken  and now it got fixed

---

