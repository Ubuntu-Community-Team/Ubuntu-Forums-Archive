---
title: "Kubuntu and Gnome Menu"
date: 2005-04-09
forum: Desktop Environments
---

### Post by fordfan753 on 2005-04-09
Today I installed Ubuntu 5.04 on my box. I thought I'd try out KDE on Ubuntu so I also installed kubuntu-desktop, but I have one simple problem...I don't want my KDE apps clogging up the Gnome menu, and I can't edit the Gnome Menu. I have found a few Menu Editting tools, but so far none have had the ability to delete stuff...

Anyway, someone must have had this problem before me, please, how did you solve it?

---

### Post by theChauvinist on 2005-04-09
There is a menu editor for GNOME that will delete things, but I'm not currently in a GNOME desktop, nor can I get to one until later today to check what it's called. It *might* be [this](http://www.gnomefiles.org/app.php?soft_id=867) one, but I can't quite figure out from it's description whether or not it can remove items.

Alternatively, you could try deleting the .desktop files, but I'm not 100% sure that that's a very good way of doing it.

I'll check back to this thread when I'm in GNOME.

---

### Post by Julius on 2005-04-09
Isn't there an option to hide menu items? That would be better :P

I also don't like the menus get after installing kde and xfce... :(

---

### Post by Knome_fan on 2005-04-09
cd /usr/share/applications/kde
sudo for i in *; do echo "OnlyShowIn=KDE;" >> $i; done

---

### Post by Nekrataal on 2005-04-09
Hey knome fan, there are syntaxis erros in the code you gave...

---

### Post by Nekrataal on 2005-04-09
```
cd /usr/share/applications/kde
sudo for i in *; do echo "OnlyShowIn=KDE;" >> $i; done
```

That code doesnt work....use this one instead:

```
cd /usr/share/applications/kde
sudo chmod a+rw /usr/share/applications/kde/*
for i in *; do echo "OnlyShowIn=KDE;" >> $i; done
sudo chmod 644 /usr/share/applications/kde/*
```

doing that the kde menus entries will go away from your gnome menus... O:)

---

### Post by fordfan753 on 2005-04-09
[QUOTE=Nekrataal]```
cd /usr/share/applications/kde
sudo for i in *; do echo "OnlyShowIn=KDE;" >> $i; done
```

That code doesnt work....use this one instead:

```
cd /usr/share/applications/kde
sudo chmod a+rw /usr/share/applications/kde/*
for i in *; do echo "OnlyShowIn=KDE;" >> $i; done
sudo chmod 644 /usr/share/applications/kde/*
```

doing that the kde menus entries will go away from your gnome menus... O:)[/QUOTE]
 Thanks, I did that, worked fine...Now I only have gnome apps in my gnome menu :D
It looks as clean and compact as it did before KDE was ever installed

---

### Post by Nekrataal on 2005-04-10
Im glad it worked, always good to help :D

---

### Post by jonny on 2005-04-11
Brilliant.

---

### Post by gunnyman on 2005-04-11
Thanks 
this was much faster than using the menu editor.

---

### Post by MaX on 2005-06-18
[QUOTE=Knome_fan]cd /usr/share/applications/kde
sudo for i in *; do echo "OnlyShowIn=KDE;" >> $i; done[/QUOTE]
 This works fine for me, but how do I do the opposite?

eg. Remove One occurrence of OnlyShowIn=KDE.

I happened to run this command on my gnome entries you see.

---

