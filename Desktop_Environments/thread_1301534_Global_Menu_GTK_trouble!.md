---
title: "Global Menu GTK trouble!"
date: 2009-10-26
forum: Desktop Environments
---

### Post by exaviorn on 2009-10-26
Hey,
A month ago I decided to, (for a bit of fun) change my linux theme and turn it into a mac using Mac4lin, I followed a tutorial somewere on the internet and it all worked.

However the new mac theme wasnt for me so I uninstalled everything using the mac for lin uninstall script and manualy apt-get remove. 

One of those programs I manualy removed was globalmenu-gnome.

now though, whenever I update or install an app, this line sometimes appears on the terminal:
```
Gtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: cannot open shared object file: No such file or directory

```

It might list something else different,but usually along the terms of failed to load module.

Will this prevent any upgrades to karmatic? I was thinking of trying the latest beta?

Thanks
Exaviorn

---

### Post by Giblet5 on 2009-10-26
Try looking at your ~/.xsession-errors file.

It should have the details.

---

### Post by gnuisancev3 on 2009-10-26
I'm not sure how mac4lin goes for it, but i know that you used to have to patch gtk2 in order to get the global menu installed and working.  You will probably see problems stemming from this until you completely remove and reinstall gtk2.

---

### Post by exaviorn on 2009-10-26
Yes, I checked the file

The phrase:
```
Gtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: cannot open shared object file: No such file or directory

```
crops up every few lines.

How do I stop it?

---

### Post by exaviorn on 2009-10-26
> **gnuisancev3 said:**
> I'm not sure how mac4lin goes for it, but i know that you used to have to patch gtk2 in order to get the global menu installed and working.  You will probably see problems stemming from this until you completely remove and reinstall gtk2.

Basicaly I followed this [guide]("http://maketecheasier.com/turn-your-ubuntu-intrepid-into-mac-osx-leopard/2009/01/08")

All I did was use alien to install the .rpm, I'm wondering if there is a reference to Global menu still somewhere in a config file :confused:

---

### Post by Giblet5 on 2009-10-26
Probably in your config somewhere...

You can find out by creating a test user, logging in as that user, and seeing if that test user gets the error.

You can try searching for it in your normal user's account via ```
find $HOME -type f -exec grep -l global {} \;
```

and editing out any found references to that stuff.


Pro Tip: anytime you need to install an rpm file, you're trying to run code that was built for redhat linux code on your ubuntu box and you might regret it.

---

### Post by exaviorn on 2009-10-26
> **Giblet5 said:**
> Probably in your config somewhere...

You can find out by creating a test user, logging in as that user, and seeing if that test user gets the error.

You can try searching for it in your normal user's account via ```
find $HOME -type f -exec grep -l global {} \;
```

and editing out any found references to that stuff.


Pro Tip: anytime you need to install an rpm file, you're trying to run code that was built for redhat linux code on your ubuntu box and you might regret it.

Thanks!
the other user test proved that its just affecting my user - typing gedit into terminal didnt provoke any warnings.

however your second suggestion was strange - the output was mostly browser cache, it then outputted wine config files and other strange program configs, surely a single program can't be in so many apps: some ive only installed reciently:confused:

---

### Post by Giblet5 on 2009-10-26
> **exaviorn said:**
> Thanks!
the other user test proved that its just affecting my user - typing gedit into terminal didnt provoke any warnings.

however your second suggestion was strange - the output was mostly browser cache, it then outputted wine config files and other strange program configs, surely a single program can't be in so many apps: some ive only installed reciently:confused:

The find command I posted just gives clues.

This will narrow the search (a lot) to just the main config directories in your account: ```
find $HOME/.gconf $HOME/.gnome2 $HOME/.config -type f -exec grep -l global {} \;
```

Good luck.

---

### Post by exaviorn on 2009-10-26
> **Giblet5 said:**
> The find command I posted just gives clues.

This will narrow the search (a lot) to just the main config directories in your account: ```
find $HOME/.gconf $HOME/.gnome2 $HOME/.config -type f -exec grep -l global {} \;
```

Good luck.

Thanks, Ive found at least one reference so far, however is it safe to just remove from the file e.g:

(home).gconf/apps/gnome_settings_daemon/gtk-modules/%gconf.xml


```
<?xml version="1.0"?>
<gconf>
        <entry name="globalmenu-gnome" mtime="1252692989" type="bool" value="tr$
</gconf>
```

---

### Post by adisk on 2012-06-14
Look at ```
/etc/profile.d/globalmenu.sh
```
You can remove it.

---

### Post by lisati on 2012-06-15
Back to sleep, old thread. A lot can happen in 3 years.

---

