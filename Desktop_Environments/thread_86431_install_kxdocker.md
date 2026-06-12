---
title: "install kxdocker"
date: 2005-11-05
forum: Desktop Environments
---

### Post by Josef K. on 2005-11-05
since kxdocker in ubuntu repository is _old_ I've downloaded (lib)kxdocker source and compile sudo -i 
./configure
make
checkinstall
everything seemes fine, but... where is kxdocker?! I just have a /usr/share/apps/kxdocker directory with some icons and plugin, but no command anywhere :confused: how am I supporsed to start this *thing* ?!

---

### Post by Freddy on 2005-11-05
If you compile with only ./configure you have to find the .bin file and start the dock by doubleclicking it and if you want it to start with kde, you would have to put a symlink of the .bin inside .kde/autostart.

I recommend that you uninstall your dock and use:
```
./configure --prefix=`kde-config --prefix`
```
Now the configure script will ask kde-config where to install and put the files, then you can start kxdocker through the command "kxdocker" and when you restart kde with it on, it will pop up when you boot your desktop.   /// Freddan

---

### Post by Josef K. on 2005-11-05
it worked! :D 
even if I had to change config file ownership by hand (was assigned to root :confused:)

---

### Post by Freddy on 2005-11-05
You could simply move the config file to your homefolder and use it from there and you would have a backup to.   /// Freddan

---

### Post by Josef K. on 2005-11-05
the config was generated in my home directory but with root ownership :confused: that's why I'd to change ownership by hand although now I still can't customize dock bar (restarting it go back to default :???: )

seems I should look for a precompiled version or find an other docker :(

---

### Post by Freddy on 2005-11-05
No I wouldn't suggest you using the .deb pack, it's rather old and awful. Just save your config file anywhere in your home folder and use that one instead of the default one. You know how to enter the configurator ?   /// Freddan

---

### Post by Josef K. on 2005-11-06
dunno why :P but after recompiling seems to work now, even if the systray icon won't render :( (instead of an apple with tux inside I've a rounding circle (like the waiting cursor))

just one more thing:
if I remove icons with right click mouse they come back if I restart, if I remove them via configurator everything works fine
so just wondering how remove directory icons (alias in configurator?) since they came back after restart :confused:

this app seems to me a bit too buggy :(

---

### Post by Freddy on 2005-11-06
> dunno why :P but after recompiling seems to work now, even if the systray icon won't render  (instead of an apple with tux inside I've a rounding circle (like the waiting cursor))
That is the new systray icon.

> if I remove icons with right click mouse they come back if I restart
Open up your configurator, go to tab alias and disable the classname by choosing disable :).   /// Freddan

---

