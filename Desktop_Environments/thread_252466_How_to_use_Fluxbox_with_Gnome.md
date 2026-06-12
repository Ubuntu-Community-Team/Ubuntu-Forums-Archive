---
title: "How to use Fluxbox with Gnome?"
date: 2006-09-06
forum: Desktop Environments
---

### Post by WalmartSniperLX on 2006-09-06
Hey I just got fluxbox and I have a few questions about it. Please can anyone help me out and answer them?

1) How do you get ur menus in fluxbox
2) How do you get ur applications and folders from gnome in fluxbox

And that is all I can think of at the momment lol. They're pretty generalized so I couldn't think of more ](*,) . Thanks

---

### Post by lagagnon on 2006-09-06
fluxbox is a minimalist window manager - designed simply to manage your windows easily, quickly, without a lot of resource useage, and it is much faster than Gnome. However, it does not automatically generate menu items for you. The fluxbox menu is created with the ~/.fluxbox/menu text file (where ~ represents your home directory). Have a look at that file and you will see how menu items are created - the syntax is easy. 

The easy way to autogenerate menus for fluxbox is to use mmaker (menumaker). [http://menumaker.sourceforge.net/](http://menumaker.sourceforge.net/)

I'm not sure if there is a Ubuntu package for it - search with synaptic.

---

### Post by kerry_s on 2006-09-06
it's installed all ready, do> update-menus <make sure you change the "/.fluxbox/menu" to point to your "/.fluxbox/fluxbox-menu" in your home directory instead of /etc/X11/fluxbox/fluxbox-menu

---

### Post by WalmartSniperLX on 2006-09-06
Awesome! Thanks you guys! :D

---

### Post by WalmartSniperLX on 2006-09-06
> **kerry_s said:**
> it's installed all ready, do> update-menus <make sure you change the "/.fluxbox/menu" to point to your "/.fluxbox/fluxbox-menu" in your home directory instead of /etc/X11/fluxbox/fluxbox-menu

I tried that but im still not getting all my ubuntu menu objects in the menu in fluxbox ](*,)

---

### Post by kerry_s on 2006-09-07
What do you mean, the icons? Or are you wanting to make a custom menu?
Can you be more clear on exactly what you want?

---

### Post by WalmartSniperLX on 2006-09-07
> **kerry_s said:**
> What do you mean, the icons? Or are you wanting to make a custom menu?
Can you be more clear on exactly what you want?

sorry man its so hard for me to explain. You know the Applications, Places, and System icons on the top menu in ubuntu? well how do i get all of those in Fluxbox? 

The only thing i can seach on the fluxbox menus is the Debian folder/menu entry :S

---

### Post by kerry_s on 2006-09-07
Hmmm, you can either make menu entries for them or use the gnome-panel in fluxbox.

 1. [http://fluxbox-wiki.org/index.php/Howto_edit_menu](http://fluxbox-wiki.org/index.php/Howto_edit_menu)

 2. in terminal> gnome-panel &
if you want to launch it every time add that command to /.fluxbox/startup

---

