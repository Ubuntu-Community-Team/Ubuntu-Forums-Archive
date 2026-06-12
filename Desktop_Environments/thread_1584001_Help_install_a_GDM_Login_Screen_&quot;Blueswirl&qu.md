---
title: "Help install a GDM Login Screen &quot;Blueswirl&quot;"
date: 2010-09-28
forum: Desktop Environments
---

### Post by georgekhry on 2010-09-28
I have just downloaded a new Login screen from 

[http://gnome-look.org/content/show.php/Blue+Swirl?content=30846](http://gnome-look.org/content/show.php/Blue+Swirl?content=30846)

I can't seem to figure how to install it any ideas ?

I am using Ubuntu 10.04

---

### Post by ankspo71 on 2010-09-28
Hi,
Ubuntu doesn't have a graphical way to install GDM themes, so you will have to install an outside application. Here's one of them that I know of...
[http://www.webupd8.org/2010/03/gdm2setup-is-now-available-for-ubuntu.html](http://www.webupd8.org/2010/03/gdm2setup-is-now-available-for-ubuntu.html)
One of the commenters in the link says that installing 'xplash' is required if you want to change the background too. I can't tell you how well it works though, because I use the Kubuntu desktop which doesn't use GDM. 
Hope this helps.

PS. Those commands in the link above are there for you to copy and paste into your terminal to install the application. When done you will find a start menu entry for it at System > Administration > "Login Screen (GDM2Setup)".

---

### Post by Mr_VeRiTy on 2010-09-28
You cant change the GDM theme in 10.04 (as far as I know), but you can change the wallpaper and gtk theme by following these steps:

(1) Copy and Paste "sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow/" Into the terminal without "quotes" and enter your password.

(2) Logout. When you see the login screen, the appearance preferences window will appear, it will let you change to look of the login screen (including wallpaper, icons, mouse, and window border)

(3) Once you have customized the login screen close the appearance window and login.

(4) Now just copy and paste "sudo rm /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop" into the terminal (without "quotes") and put your password in. Done.

---

