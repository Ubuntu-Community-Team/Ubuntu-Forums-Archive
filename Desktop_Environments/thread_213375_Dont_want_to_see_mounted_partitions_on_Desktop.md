---
title: "Dont want to see mounted partitions on Desktop"
date: 2006-07-11
forum: Desktop Environments
---

### Post by dhruv_1884 on 2006-07-11
Hi,

I did a fresh install for dapper, and partitioned the hardisk manually, 

everythings fine, but i dont like their look on my desktop, 
firstly the partitions have got named hda1, hda2 and so on, they were mounted automatically,i dont like the names, i tried using the command mv but the terminal said that the resource was busy,

i dont like the icons either, i was wondering if i could use icons like the one on mac

and even if i get the icons , i'd prefer accesinf them through My Computer

any suggestions guys

thanks 

regards

dhruv

---

### Post by firebadger on 2006-07-11
I asked something similar here [http://www.ubuntuforums.org/showthread.php?t=202383]("http://www.ubuntuforums.org/showthread.php?t=202383") but didn't get a reply.

---

### Post by Blashyrk on 2006-07-11
Hi!

If you want to take away all your mounted partitions icons from your desktop you only need to run gconf-editor and go to apps -> nautilus -> desktop There you will find some options about icons on the desktop, by default volumes_visible is set to true, you only have to turn it off. that's all!!

And abot the mac style icons have a look to [http://www.gnome-look.org/]("http://www.gnome-look.org/") or [http://art.gnome.org/]("http://art.gnome.org/") There are lots of icons themes for your gnome desktop. Some of theme with the mac style.

Have a good time!!

---

### Post by f1dave on 2006-07-11
I have a couple of tips, assuming you're using KDE.

1. You can right click on the desktop and go "configure desktop". Under behavior, you can modify a whole pile of things including what icons get displayed.

2. If you want to change your icon theme, go to [www.kde-look.org](www.kde-look.org) and look under icons, there's a wealth of things including mac-like looks.

Now if you're using gnome, unfortunately I haven't used that in a while and can't be of much help bar recommending gnome-look.org or art.gnome.org

edit: beaten by a minute! A MINUTE I SAY!

---

### Post by mlind on 2006-07-11
For GNOME, gconf key is /apps/nautilus/desktop/volumes_visible key.

---

### Post by dolby on 2006-07-11
press Alt+f2

run gconf-editor

go to apps->nautilus->desktop

uncheck volumes visible

---

### Post by firebadger on 2006-07-11
Thanks, the gconf-editor solution was exactly what I was looking for.

---

### Post by Wolki on 2006-07-11
> **dhruv_1884 said:**
> everythings fine, but i dont like their look on my desktop, 
firstly the partitions have got named hda1, hda2 and so on, they were mounted automatically,i dont like the names, i tried using the command mv but the terminal said that the resource was busy,

i dont like the icons either, i was wondering if i could use icons like the one on mac

and even if i get the icons , i'd prefer accesinf them through My Computer

volumes_visible will work, but also disable desktop icons for cds and usb-sticks, which some people don't like. As far as I know, nautilus will only show stuff that's mounted into /media or /mnt on the desktop, so you could just mount them somewhere else.

You should be able to set more sensible names for your partitions with tune2fs or similar software (do **NOT** use gparted to set disk labels! it's sometthing different and will just delete your stuff)

You can set custom icons one by one by using the properties window in nautilus (click on the button htat contains the icon). You probably can change them for all, but that might take some work (basically, creating an icon theme based on the current one and changing what you want). You'll probably find some pre-built osx-style icon themes on gnome theming sites though.

---

### Post by firebadger on 2006-07-11
It would be nice if the auto-mount stuff still appeared on the desktop.  Will it appear in the Places menu?  I don't have anything suitable with me to try an experiment just now.

---

