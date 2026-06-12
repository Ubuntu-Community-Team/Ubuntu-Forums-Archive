---
title: "goal: boot into console, with startx loading Kdm?"
date: 2005-07-27
forum: Desktop Environments
---

### Post by nasaiya on 2005-07-27
I can't seem to figure out how to make startx load kdm. i removed gdm from rcx.d with update-rc.d -f gdm remove but still if i boot into a console (which is the goal) whenever i type startx up comes gnome!  

i just want to be able to start with a console and then run kubuntu if i need to with startx. 

Is this possible???
Please help!

---

### Post by tonysathre on 2005-08-08
maybe this link will help:

[http://kde-cygwin.sourceforge.net/kde1/faq.php#A1](http://kde-cygwin.sourceforge.net/kde1/faq.php#A1)

---

### Post by arjaybe on 2005-08-08
[QUOTE=nasaiya]I can't seem to figure out how to make startx load kdm. i removed gdm from rcx.d with update-rc.d -f gdm remove but still if i boot into a console (which is the goal) whenever i type startx up comes gnome!  

i just want to be able to start with a console and then run kubuntu if i need to with startx. 

Is this possible???
Please help![/QUOTE]

The display manager (kdm/gdm) doesn't determine the desktop (kde/gnome.)  You can run gnome from kdm and vice versa.  If you want kdm, install it and it should insert itself into /etc/X11/default-display-manager.

---

### Post by Goofy_2 on 2005-09-09
Installed:  Kubuntu 5.04

According to my etc/X11/default-display-manager is 'kdm' default.
Nevertheless Gnome instead of KDE will be started 'by default' when I use the command 'startx' when logged in as a normal user (without X).

The following is working in my case.
Don-t know if  it's 'best solution'....

Logged in as normal user in the bash-shell you can use mcedit, pico, etc.

$  cd                  (goto your home-dir)
$  mcedit .xinitrc
    exec startkde
    # End of file

$  chmod 644 .xinitrc  (probably not necessary)
$  startx           

Now  you will get the KDE desktop environment.

---

