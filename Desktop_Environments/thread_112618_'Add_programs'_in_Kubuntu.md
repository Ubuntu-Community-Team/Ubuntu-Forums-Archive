---
title: "'Add programs' in Kubuntu?"
date: 2006-01-04
forum: Desktop Environments
---

### Post by Mathias-K on 2006-01-04
I started out in Ubuntu Breezy, where i learned about Synaptic, but also used the feature Add programs to clean my menus of the unused programs, and to add new ones.

I can't seem to find this feature in Kubuntu :)

---

### Post by taseal on 2006-01-04
adept :)

you can get to it by typing sudo adept in the terminal

---

### Post by Mathias-K on 2006-01-04
Perhaps i did not express myself clearly. I have already updated from all the repositories in Adept. I'm looking for a way to manage which programs to have in my KDE menus. In ubuntu, this is called 'Add programs' and is very smart. I'm looking for a feature like this in Kubuntu.

---

### Post by taseal on 2006-01-04
[QUOTE=Mathias-K]Perhaps i did not express myself clearly. I have already updated from all the repositories in Adept. I'm looking for a way to manage which programs to have in my KDE menus. In ubuntu, this is called 'Add programs' and is very smart. I'm looking for a feature like this in Kubuntu.[/QUOTE]

ohhh....

i'm not sure if there is something like that with kubuntu unfortunetly :(

I just use [www.kde-apps.org](www.kde-apps.org)

if the program is purdy known, its most likely in the repos anyways, so i just do a sudo install...

---

### Post by Omnios on 2006-01-04
Not on KDE right now but think it was right click menu button and there should be a menu manager there

---

### Post by taseal on 2006-01-04
you can use adept thing to uninstall programs if you didnt know

but no 'add applications' for KDE :(

I used it with ubuntu alot too, it was awesome... just got used to kde-apps.org now...

---

### Post by Adrian on 2006-01-04
[QUOTE=Omnios]Not on KDE right now but think it was right click menu button and there should be a menu manager there[/QUOTE]

If the terminal is your friend, you can also use the command "kmenuedit" to launch the very same editor ;)

(...well, I usually do that in the "Run Command..." dialog)

---

### Post by Mathias-K on 2006-01-05
Thanks for your replies. It seems i was right about it not being in KDE, unfortunately. But i think i'll stay with Kubuntu as long as it is much prettier than Ubuntu :)

---

### Post by taseal on 2006-01-05
I would say we will see something similar with kubuntu in the next release

---

### Post by dawynn on 2006-01-05
I can't speak for the gnome side, but its been my experience in KDE that most packages will automatically add or remove themselves from the menu as they are added or removed from the apt repository (whether that be via aptitude (command-line utility), synaptic, kynaptic, kpackage, adept, etc).  In the few instances where a program does not update the menu, kmenuedit is the way to go.

Although kmenuedit does not list itself in the menus (not sure why), you can easily reach it, either by asking for it from the "run command" item, or from a terminal, or simply by right-clicking on any other menu item and choosing appropriate options (like add -- item to menu).

If a specific package does *not* add / remove the appropriate menu commands for KDE, it is a failing / bug of the package, and not something to make some kind of "add programs" utility for.  If the package itself can't figure out what programs it installs, how is some automated utility going to do it?

---

### Post by Adrian on 2006-01-05
[QUOTE=dawynn]Although kmenuedit does not list itself in the menus (not sure why), you can easily reach it, either by asking for it from the "run command" item, or from a terminal, or simply by right-clicking on any other menu item and choosing appropriate options (like add -- item to menu).[/QUOTE]

I didn't understand why before either. However, some posts up, Omnios delivered an explanation. You don't have to right click on a menu item inside the menu (which I first thought). You can right click on the K menu button itself, and then choose the "Menu Editor" option.

---

### Post by veloct on 2006-01-05
If you right click on the K menu button you have an option to change the menu.  It can also be access through system settings or kcontrol

---

