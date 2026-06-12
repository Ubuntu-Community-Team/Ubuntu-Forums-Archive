---
title: "customization questions"
date: 2006-08-02
forum: Desktop Environments
---

### Post by rotten777 on 2006-08-02
i'm stuck. i've installed themes and got **almost** everything the way i want.

why is this orange when everything else is graphite/silver? where can i change it?
[IMG]http://www.hooklinesinker.org/ubuntu/orangetaskbar.png[/IMG]


why is this blue menu blue instead of graphite/silver? where can i change it?
[IMG]http://www.hooklinesinker.org/ubuntu/bluemenu.png[/IMG]

how can i change the color of selected text? it's the orange/brownish default ubuntu color.

how can i change the color of the background before gnome loads the wallpaper? its the default nasty brown.


thanks for any help!

---

### Post by scxtt on 2006-08-02
> how can i change the color of the background before gnome loads the wallpaper? its the default nasty brown.you can select the color in the same area you select a wallpaper ...

---

### Post by rotten777 on 2006-08-02
> **scxtt said:**
> you can select the color in the same area you select a wallpaper ...


i've already changed it to blue :-k

---

### Post by sjbrun on 2006-08-03
> **rotten777 said:**
> 
how can i change the color of the background before gnome loads the wallpaper? its the default nasty brown.


The background color can be changed in the login window preferences dialog.
To get there click on System -> Administration -> Login Window

---

### Post by rotten777 on 2006-08-03
> **sjbrun said:**
> The background color can be changed in the login window preferences dialog.
To get there click on System -> Administration -> Login Window


awesome thanks.

do you know if this is stored in a flat or XML file somewhere?

---

### Post by sjbrun on 2006-08-03
> **rotten777 said:**
> 
do you know if this is stored in a flat or XML file somewhere?

I don't know where that setting is stored. Probably in a hidden file somewhere in your home directory.

---

### Post by rotten777 on 2006-08-03
ok the login screen thing worked.

any idea about this? (ignore the weird jagged edges)
[IMG]http://www.hooklinesinker.org/ubuntu/selectarea.png[/IMG]

the select area and text on icons (when selected) is still the default color.

---

### Post by sjbrun on 2006-08-04
> **rotten777 said:**
> 
the select area and text on icons (when selected) is still the default color.

For that I think you need to edit the gtkrc file of your selected theme.
```
gedit ~/.themes/name_of_your_theme/gtk-2.0/gtkrc
```

Change this line near the top:
```
base[SELECTED]    = "#xxxxxx"
```

to:
```
base[SELECTED]    = "#628cb2" # Blue
```

---

