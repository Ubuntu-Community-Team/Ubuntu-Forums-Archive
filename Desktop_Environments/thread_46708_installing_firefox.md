---
title: "installing firefox"
date: 2005-07-05
forum: Desktop Environments
---

### Post by richardspirit on 2005-07-05
I'm having trouble getting firefox to install. 

I open the terminal su into root and then I run 
#cd firefox-installer 
# ./firefox-installer
but I keep getting this error
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firefox-installer-bin:26851): Gtk-WARNING **: cannot open display:

how do I fix this?

---

### Post by jasmuz on 2005-07-05
[QUOTE=richardspirit]I'm having trouble getting firefox to install. 

I open the terminal su into root and then I run 
#cd firefox-installer 
# ./firefox-installer
but I keep getting this error
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firefox-installer-bin:26851): Gtk-WARNING **: cannot open display:

how do I fix this?[/QUOTE]
 I have no idea how you can fix it, but you could add the Ubuntu Backports and download the latest from the repositories.

add these to your list:
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by ltmon on 2005-07-05
I agree with the above post that you should really use backports if you want the most recent version of Firefox ....

However, your problem is that by default you cannot run X programs as root.  One of several ways to fix this is to edit /root/.bashrc to contain the following line:

export XAUTHORITY=/home/<username>/.Xauthority

where username is your own username.

L.

---

