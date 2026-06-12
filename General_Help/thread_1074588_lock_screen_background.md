---
title: "lock screen background"
date: 2009-02-19
forum: General Help
---

### Post by metalmaniac248 on 2009-02-19
the other day i installed a theme .deb package, it installed a GTk theme, some a wallpaper, and some other visual things, i didnt particularly like the theme once installed so i removed it, however now, when i lock my computer, the background that came with the theme is the background for the lock screen, how can i change this?


thanks,

---

### Post by iKonaK on 2009-02-19
Frankly i didn't knew you can change the lock screen backround color but if you say you installed a .deb file you should try open the .deb GUI installer and go to the tab with the included files and search from there; hope it sets you on a good course :)

---

### Post by S3NATOR on 2009-02-19
I'm having this same problem. I installed a gtk theme and decided I didn't like it and changed back to another theme. Now when I lock my computer it shows the wallpaper from the gtk theme I installed. I've been trying to find a way to change the wallpaper or disable it for awhile now with no success. Before I installed the theme it was always just a black background. I'll post back if I find a solution.

I guess there is no option in "Appearance" or something that allows you to change this?

S3N

---

### Post by metalmaniac248 on 2009-02-20
problem solved,

seen as it was installed from a .deb package, i found it in synaptic, it was called something like "ultimate-edition-theme-pack-all" clicked complete removal, and presto the ugly lock screen is banished


hope this helps

---

### Post by S3NATOR on 2009-02-20
Ha! Yea thats the same theme I was trying to get rid of. Removing it with Synaptic Manager works. Now I wish I knew how to use whatever wallpaper I wanted for my lock screen.

Thanks,
S3N

---

### Post by metalmaniac248 on 2009-02-21
well. it seems that xlockscreen dosnt have theme support, for now anyway but i found this link, seems this guy has developed a way to do it,

[http://www.swanson.ukfsn.org/xss/]("http://www.swanson.ukfsn.org/xss/")


seems allot of fuss just for the lock screen, though

---

### Post by metalmaniac248 on 2009-02-21
i dont really know what i would be lookin for but, i you could try download one of these theme debs extract it and go through the contents to find how the creator set it up to apply a background to the lock screen,

---

### Post by metalmaniac248 on 2009-02-22
found this too


if you go to gnome look and look under screensavers, most of the things there are lock screen themes, if you see one you like download it extract it and copy the contents to /usr/share/gnome-screensaver

then open gconf-editor

```
gksudo gconf-editor
```


go to apps then gnome-screensaver and change the lock_dialog_theme value to whatever it says on the page you downloaded it from.

---

### Post by d3v1150m471c on 2009-12-17
I've had no success with installing the lock screen backgrounds using gconf-editor, however i found an easy way to do it manually. First, access usr/share/backgrounds and find the size and name of the lockscreen background. Second, grab a picture in the same format and size of the default picture. You're going to need to save the default picture elsewhere on your computer for the next step OR YOU WILL LOSE THIS FILE. Select the new background you want to use and save it as the same name as the default picture. IE say the default picture is named ooboontoo.jpg so on your desktop or in your pictures folder you will save the new background with the exact same name, ooboontoo.jpg. Next, go to your terminal and enter your file manager as root. 

gksudo nautilus

Navigate to the usr/share/backgrounds and drag and drop the new image and replace it :)
Problem solved.

---

### Post by unadulterated on 2011-03-14
I did all this but its not doing it.. using ubuntu 10.10 and trying the use the elementary ([http://gnome-look.org/content/show.php/elementary+lock+screen?content=107792](http://gnome-look.org/content/show.php/elementary+lock+screen?content=107792)) lock screen, any ideas?

> **metalmaniac248 said:**
> found this too


if you go to gnome look and look under screensavers, most of the things there are lock screen themes, if you see one you like download it extract it and copy the contents to /usr/share/gnome-screensaver

then open gconf-editor

```
gksudo gconf-editor
```


go to apps then gnome-screensaver and change the lock_dialog_theme value to whatever it says on the page you downloaded it from.

---

