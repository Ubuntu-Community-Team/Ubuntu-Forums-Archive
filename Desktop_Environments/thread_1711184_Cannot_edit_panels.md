---
title: "Cannot edit panels"
date: 2011-03-21
forum: Desktop Environments
---

### Post by arif920629 on 2011-03-21
Hi everyone. I have this problem that i can't seem to edit panels. I only get 'help' and 'about panels' when I right click a blank space on the panel. Any solutions?

---

### Post by Krytarik on 2011-03-21
Are you trying to do that with the "Netbook Edition"?

If so, the only way to modify the panel is to manually edit the file "/var/lib/gconf/une.mandatory/%gconf-tree.xml". These are system-wide settings.

I had to do that to "free" the "Window Picker Applet". ;-)

---

### Post by arif920629 on 2011-03-22
No, I'm using normal Lucid. using compiz as window manager.In addition I also have to run "compiz -replace" sometimes after booting up the PC because there are no windows D:

---

### Post by Krytarik on 2011-03-23
That's unusual then. Please check if the issue also occurs in a fresh user account, therefore add a new user via "System -> Administration -> Users and Groups" and then login with those.

---

### Post by celldweller1591 on 2011-03-23
Try this very carefully, there are two methods :- 
1) Create a New user with Administrator privileges and migrate all your important documents from old user and delete the old user. 

2) For the alternative method, you will have to use "Ubuntu's Virtual console" i.e press CTRL+ALT+F1. Login to your account and type the following command :-

> rm -rf .gnome .gnome2 .gconf .gconfd .metacity

Now press ALT+F7 to return to your desktop and it should now be working fine with default setup. Else reboot and it should work now. 

#The whole point behind both of these processes is that Gnome desktop depends upon various configuration files which are user specific. Any changes a user does, are written to these files. Creating a new user or deleting these will reconfigure them to default and that will solve the problem.

---

### Post by Krytarik on 2011-03-23
> **celldweller1591 said:**
> Try this very carefully, there are two methods :- 
1) Create a New user with Administrator privileges and migrate all your important documents from old user and delete the old user.
You shouldn't even consider this before you know that a new user really fixes the issue.
But even then there are numerous possible ways to fix your existing user account, the new user test only helps to narrow it down.
> **celldweller1591 said:**
> 2) For the alternative method, you will have to use "Ubuntu's Virtual console" i.e press CTRL+ALT+F1. Login to your account and type the following command :-

>  rm -rf .gnome .gnome2 .gconf .gconfd .metacityNow press ALT+F7 to return to your desktop and it should now be working fine with default setup. Else reboot and it should work now. 

#The whole point behind both of these processes is that Gnome desktop depends upon various configuration files which are user specific. Any changes a user does, are written to these files. Creating a new user or deleting these will reconfigure them to default and that will solve the problem.
Ok, I seem to have to keep on stating this: You don't need to **reset  your entire Gnome environment** in order to make your panels work! You could at best run the following command to reset just your panels, run it in a terminal:
```
gconftool-2 --recursive-unset /apps/panel && killall gnome-panel
```

---

### Post by arif920629 on 2011-05-21
@Krytarik

LOL sorry for the very very (2 months) late reply. Your method worked for me. Thanks =D

---

