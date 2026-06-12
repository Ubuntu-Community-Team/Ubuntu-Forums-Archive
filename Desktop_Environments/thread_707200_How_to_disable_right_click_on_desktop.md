---
title: "How to disable right click on desktop"
date: 2008-02-25
forum: Desktop Environments
---

### Post by keenboy on 2008-02-25
Hello,

I am building an ltsp server and wish to disable 'right click' on the desktop for all users accept my admin user. In fact I want to lock down the whole profile if I can to stop users changing things like desktops and menus etc.

I have looked at the gconf-editor but I cannot find the option to do it.

Does anybody know how to do this?

Thanks

---

### Post by erginemr on 2008-02-25
There is a Gnome lockdown program "pessulus", that I know, can disable a number of features on a Gnome desktop:
[http://www.linux.com/feature/62060](http://www.linux.com/feature/62060)

You can install it with
```
sudo aptitude install pessulus
```

You may find it useful...

---

### Post by erginemr on 2008-02-25
There is also "sabayon", which manages user profiles and their rights on a more global level:
[http://www.linux.com/feature/114319](http://www.linux.com/feature/114319)

It is also in the synaptic repositories.

---

### Post by keenboy on 2008-02-25
Thanks for the responses however I have looked at both of them.

Pessulus doesn't have the option to lock the desktop down, only panel.

Sabayon crashes all of the time, I think I get to edit one thing before it kicks me out, which is very annoying!!

I have also looked at gconf-editor, this doesn't seem to allow the desktop to locked own.

I need a 'kiosk' type application, I know sabayon is supposed to do this but obviously it doesn't work..............a little bit like how ltsp-manager doesn't work either AAAAAAHHHH](*,)

---

### Post by aanderse on 2008-02-25
have you ever tried using xfdesktop (the xfce desktop manager) instead of the default gnome one? you can make it so the user can't right click on the desktop with that. the one downside being that it doesn't have the exact same icon interface that gnome does. might be worth taking a look at though, just incase.

good luck

---

### Post by keenboy on 2008-02-25
I have used xubuntu before, it's a great distro however I really want to stick with ubuntu.

I have read posts explaining that sabayon has the ability to do what I want, if it worked. I am under the impression that sabayon does the same things as gconf-editor in terms of system changes.

Is there a disable right click option in gconf-editor that I have missed somewhere? My server is ready to roll apart from this little snag!!

---

### Post by erginemr on 2008-02-25
Please try the final advice in this thread:
[http://ubuntuforums.org/archive/index.php/t-515689.html](http://ubuntuforums.org/archive/index.php/t-515689.html)

Posted by **anselm13**:
> This document was helpful to me when making a kiosk out of ubuntu and gnome:
[http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/desktop-guide/ch-ddg-lockdown.html](http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/desktop-guide/ch-ddg-lockdown.html)

Also, to disable the desktop menu (i.e. the menu that appears when you right click on the desktop), run gconf-editor. Within gconf-editor ensure the "/apps/nautilus/preferences/show_desktop" option is unchecked.

---

### Post by keenboy on 2008-02-27
I have read this post and I have picked up some useful tips. 

However 

```
Within gconf-editor ensure the "/apps/nautilus/preferences/show_desktop" option is unchecked.
```

just completely disables the desktop. This means all of the application launchers disappear, I can cope with that. I don't think this is important.

It would be good if ubuntu/pessulus had a similar locking down method for the menus as it has for the panels. At the moment a non admin user can add whatever they like to their menus which I find a bit worrying!!

---

### Post by erginemr on 2008-02-27
The Gnome menu can be edited by two applications; **"/usr/bin/alacarte"** by default or **"/usr/bin/gmenu-simple-editor"** if its absence. I have tried several alternatives including renaming these two to: "/usr/bin/alacarte2" and "/usr/bin/gmenu-simple-editor2", but every time have been welcomed with a side effect.

Unfortunately, I couldn't find any reference to either in gconf-editor, although there is a reference to "gmenu-simple-editor" as a hidden menu item (under the heading entitled as "Other") inside the Gnome menu itself.

There are also these two files **"~/.config/menus/applications.menu"** and **"~/.config/menus/settings.menu"** in a hidden subfolder of users' home directories. The best workaround in my opinion is to change the ownership of these two files to root:
```
sudo chown root:root ~/.config/menus/applications.menu
sudo chown root:root ~/.config/menus/settings.menu
```
Then, these cannot be edited or altered any more by a regular user who doesn't know the root password.

When I do this, right-click on the Main Menu and select Edit Menus, Gnome tries to load Alacarte for some 10-15 seconds, but fails miserably in the end. Of course, having no "Edit Menus" item would be much better, but this is as good as it gets and should discourage any adventurous users after a few attempts.

P.S. By the way, the natural belief in these circumstances would be to be able to edit the menu with Alt+F2 -> gksu alacarte, but this turns out to be a false belief eventually, because when you run the tool with root permissions, it refers to some other menu (possibly root's own menu).

---

### Post by keenboy on 2008-02-27
Thanks I'll give that a go and see what the results are.

It would be so good to see a 'kde kiosk' type application that works for gnome. I have seen so many people wanting similar things.

I have seen that there is some requests for pessulus that are exactly what I want, but nothing seems to be in motion.

Sabayon would be ok if it didn't keep crashing, but hey ho!

I'll just have to deploy my server and hope that these changes can be implemented later.

---

