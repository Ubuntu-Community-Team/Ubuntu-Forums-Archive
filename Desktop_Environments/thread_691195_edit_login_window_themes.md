---
title: "edit login window themes?"
date: 2008-02-08
forum: Desktop Environments
---

### Post by n-alexander on 2008-02-08
1) how to edit login window themes? Or just where to find them?

2) how to set login window resolution? It's different from session settings

thanks,
Alex

---

### Post by ajgreeny on 2008-02-08
1   Go to [http://www.gnome-look.org/](http://www.gnome-look.org/) where you will find masses of artwork and themes, etc etc for your box.

2   The various themes etc. come in a number of different resolutions, I think, so chose an appropriate one for your system.

---

### Post by tcommbee on 2008-02-08
you could try gnome-art (installable through synaptic) to browse catalogs of themes, wallpapers and gdm-themes, all directly loaded from art.gnome.org.

---

### Post by n-alexander on 2008-02-09
Thanks for pointers, it's not exactly what I was looking for, but anyway. Downloaded a few nice themes.

I was looking for the place on my file system where the installed themes were stored. Just should have made myself clearer. Found it yesterday, it's /usr/share/gdm/themes, and it's editable.

There is one remaining question: after splash and login window, it shows an empty light brown screen for a moment before loading my desktop. Where is the picture file for  that screen located? I want to edit it.

Thanks,
Alex

---

### Post by ajgreeny on 2008-02-09
> There is one remaining question: after splash and login window, it shows an empty light brown screen for a moment before loading my desktop. Where is the picture file for that screen located? I want to edit it.
You can do this with the following:-
How to change the colour of the brown splash screen that shows after I log in but before the desktop loads.  To change to light blue:-

```
sudo gedit /etc/gdm/PreSession/Default
```

look for

```
# Default value  
      if [ "x$BACKCOLOR" = "x" ]; then  
              BACKCOLOR="#dab082"  
      fi

```
and change the "#dab082" to "97A7CD" or whatever colour code you want.

```
# Default value  
      if [ "x$BACKCOLOR" = "x" ]; then  
              BACKCOLOR="#97A7CD"  
      fi

```
In this case the "#97A7cd" gives the pale blue colour I wanted.  You can experiment to get the colour you want or use the colour picker from the desktop background change dialogue box, which is how I found my colour code.

---

### Post by 1875 on 2008-02-09
System-Administration-Login Window-Local

---

### Post by tcommbee on 2008-02-09
this is better already, but i'm looking for a way to completely disable rerendering of the screen until my wallpaper gets loaded. in gdm theme documentation there's a note that enabling background="true" for the background image in the theme file would produce a seamlees transition from this image to the wallpaper (of course they are the exact same image in my case :-D )

---

### Post by snowe2010 on 2008-02-12
when i go to system...administration.. there is no tab for login window. and i went to main menu to see if i could add it to the menu and it still wasnt there. Where could it have gone?

---

### Post by n-alexander on 2008-02-12
> **snowe2010 said:**
> when i go to system...administration.. there is no tab for login window. and i went to main menu to see if i could add it to the menu and it still wasnt there. Where could it have gone?

you need to be root for this, I think

---

### Post by ajgreeny on 2008-02-13
Right click on your menu button and edit the menu.  The link to "Login Window" must have been deselected.

---

