---
title: "Help with GTK please!"
date: 2008-12-18
forum: Desktop Environments
---

### Post by macintosh on 2008-12-18
I see that my ubuntu install has some problems! When I open up normal GNOME application's my GTK themes run wonderfully but when I go to something that require admin privileges, the theme is disabled and put in place with a ugly Redmond looking theme. I tried to open the Appearance Control Panel in root and I changed the theme but it still comes up as this ugly theme! Help Please! This has been annoying me even when I was starting with Ubuntu when Hardy came out.

---

### Post by markharding557 on 2008-12-18
I have got around this by logging in to gnome as root.
to do this you must shut x down
> /etc/init.d/gdm stop

you should be on a comandline,now put the following 
> sudo -i
this will give you root and then 
> startx
you should now be in the gnome desktop as root,change the theme and then shut down x again and you will be back on the commandline type
> exit
this will change back to the normal user and then 
> startx
to get the desktop back

---

### Post by Kirky_D on 2008-12-19
Actually the problem is that root doesn't have the same themes as your user. Your themes are stored in 
```
/home/USER/.themes/
``` 
but root's themes are stored in 
```
/root/.themes/
```
So the simple solution is to copy your themes from your user directory into the root directory
```
sudo cp -r ~/.themes /root/.themes
```

You can also make a symbolic link from /root/.themes to your .themes folder, but i'm not sure how safe that would be. The above works.

---

### Post by blackened on 2008-12-19
> **Kirky_D said:**
> ...So the simple solution is to copy your themes from your user directory into the root directory
```
sudo cp -r ~/.themes /root/.themes
```

You can also make a symbolic link from /root/.themes to your .themes folder, but i'm not sure how safe that would be. The above works.

While this works, it's definitely not the best accepted method. By copying the themes into the root directory you not only increase system bloat, but you will be required to repeat this process every time you install a new theme (the new theme will be present in the user's theme directory, but not in root's). You should also create links for fonts and icons installed to your user directory.

Create symbolic links to the appropriate user folders:

```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
sudo ln -s ~/.fonts /root/.fonts
```

---

