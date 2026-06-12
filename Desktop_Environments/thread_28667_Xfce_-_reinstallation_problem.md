---
title: "Xfce - reinstallation problem"
date: 2005-04-21
forum: Desktop Environments
---

### Post by goebbe on 2005-04-21
Somehow I messed up the configuration of my Xfce-desktop and
decidet to reinstall Xfce.  :neutral: 
First I removed Xfce by:

sudo apt-get remove --purge xfce4

Then I (re) installed it by:

sudo apt-get install xfce4 

Now I have the problem that when I try to login/start a Xfce session I
just receive an error-message that the file
/etc/xdg/xinitrc 
cannot be found.

Does anybody have an idea which package I have to install/reinstall to 
get the  xfce4 specific xinitrc  back? 
Thanks a lot

---

### Post by wolovids on 2005-04-21
[QUOTE=goebbe]Now I have the problem that when I try to login/start a Xfce session I
just receive an error-message that the file
/etc/xdg/xinitrc 
cannot be found.[/QUOTE]
Shouldn't the xfce.desktop file (I think they are located in the /etc/X11/xsessions directory) be pointing to /etc/xdg/xfce4/xinitrc instead?

---

### Post by goebbe on 2005-04-21
Sorry, you are right. Here is the text of the error message:

/etc/xdg/xfce4/xinitrc  :  No such fule or directory

However there is no xinitrc in the whole /etc/xdg tree.
Does anybody know which package I have to  reinstall to get the default
xinitrc for xfce?
Thank you.

---

### Post by goebbe on 2005-04-23
It took me some time to figure out how it works - but finally
I manged to reinstall xfce:

1. logout 
2. Alt+Ctrl+F1
3. sudo /etc/init.d/gdm stop
4. sudo apt-get remove --purge libxfcegui4-3
5. sudo apt-get install xfce4
6. sudo /etc/init.d/gdm start
7. login

When I tried to remove/reinstall Xfce with the help of 
Synaptics (out of Gnome)  -  it did not work.

p.s. I am not an linux/Ubuntu expert so there may be 
easier ways to do the same thing.

---

