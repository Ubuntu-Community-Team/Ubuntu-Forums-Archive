---
title: "tightvnc to run as other than root"
date: 2005-06-08
forum: Desktop Environments
---

### Post by ubuntu_fire on 2005-06-08
I have installed tightvncserver on my box, but it requires me to install it as using sudo or becoming root.  However when I connect to the server it gives me the root desktop while I want to use my regular user desktop.  Can anyone help me?  Do I need to change this in the OS or in the tightvnc config files?

---

### Post by connellr on 2005-06-08
First off lets stop the instance of VNC server you have running as root by typing *vncserver -kill :1* 

Log into your machine as the user you want to run vncserver under.  While logged in as that user open a console and type *vncserver*.  If this is the first time you have done this you will ask you to create a password for the vnc connection.  Now you will be able to vnc in as your normal user (whatever user you start the vnc service with, is the user you vnc into the machine as).

You may then need to modify your ~/.vnc/xstartup file to start Gnome or KDE unless you just want a simple x-windows screen.

---

### Post by ubuntu_fire on 2005-06-08
This is the error I get when i try and run vncserver without sudo or becoming root.

vncserver: Wrong type or access mode of /home/eric/.vnc.

Any ideas?

---

### Post by connellr on 2005-06-09
Check the ownership and permissions for your ~/.vnc folder (ls -al ~/.vnc)
This folder should be owned by your user, and have RWX permissions for user, if it doesnt fix it with

sudo chown *yourusername* ~/.vnc/ -R
sudo chmod 700 ~/.vnc/ -R

hope this helps,
RJ

---

### Post by ubuntu_fire on 2005-06-09
Thanks RJ that did the trick.

---

