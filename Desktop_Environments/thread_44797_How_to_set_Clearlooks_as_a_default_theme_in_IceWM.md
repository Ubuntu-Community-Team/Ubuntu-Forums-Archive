---
title: "How to set Clearlooks as a default theme in IceWM?"
date: 2005-06-27
forum: Desktop Environments
---

### Post by vronskij on 2005-06-27
Hi,

When I start the IceWM, all Gtk applications have the default (not very nice) look.
This can be changed by gnome-theme-manger. I would like to set this as default look and feel when I log in.

Any ideas how to do this? 

thanks

---

### Post by ilbahr on 2005-08-18
I would be quite interested too in knowing how to do that. I will just restate your question. Is there anyway to change the default gtk theme. The default one as it says in my installation is built in the kernel.It is ugly. Is there a way to change it if we ran nautilus under other window managers such as enlightenment and icewm.

Unfourtanetly i have a rather crude trick that trigger the theme under enlightenment DR16
 i run gnome-panel
form the menu i run system>prefrences>theme

just doing that changes the theme i do not even change anything just by opening this menu i have my beloved clearlooks. Wierd eh!

---

### Post by ilbahr on 2005-08-18
I finally figured how this crude solution work
to let nautilus get your default gtk theme run in a terminal

gnome-theme-manager

you do not need to select any specific theme except once

---

### Post by ilbahr on 2005-08-28
enabling the default theme and icons can be also performed by including the line
gnome-settings-daemon 
to the window manager start up script

---

### Post by vronskij on 2005-09-01
Thanks Ibahr for your replies.
I personally still haven't figured this out. I think it must have a solution. Clearlooks is a default theme on Gnome and XFCE. It is not under Icewm and KDE. 
There has to be some conf file. The question is: where is it?

Personally I still launch gnome-theme-manager from the terminal and press Ctrl+c when the theme changes. 

Will inform when I find the clue.

---

