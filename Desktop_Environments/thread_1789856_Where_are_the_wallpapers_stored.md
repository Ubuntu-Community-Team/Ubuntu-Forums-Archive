---
title: "Where are the wallpapers stored?"
date: 2011-06-24
forum: Desktop Environments
---

### Post by garagestmarien on 2011-06-24
I have changed from Ubuntu to Xubuntu and have a problem that when I re-boot, it doesn't remember t my wallpaper.
That image is on a seperate drive and after re-boot, when I go to desktop settings, only the Xubuntu wallpapers are there and I have to add my one.
So, being a bit of a noob, I guess I could add my wallpaper to the same folder as the Xubuntu one to solve this problem.
Only, I don't know where to look to find this folder.

---

### Post by gmargo on 2011-06-24
```

$ locate xubuntu-bluebird.png
/usr/share/xfce4/backdrops/xubuntu-bluebird.png

```

---

### Post by Toz on 2011-06-24
You can also have user-specific backgrounds show up in the selection dialog by adding them to **~/.local/share/xfce4/backdrops** (you may need to create the folder if it doesn't exist).

This way you don't need to add them to the secured default location.

And if your images are on a separate drive, you can create a symlink to the drive:```
ln -s /your/separate/drive/folder ~/.loca[/share/xfce4/backdrops
```

Just be careful you don't have too many images there - there is an obvious performance penalty with drawing the selection dialog with large numbers of image files.

---

### Post by samigina on 2011-06-24
It sound like you have your image in a NTFS partition? It isnt auto-mounted.

The easy way is to copy your image to your Home/Images/ and then it will always be available for your system.

The right way is to configura your partition to automount:
Instal PySDM through the Software Center, runnit and configure your partition.

---

### Post by garagestmarien on 2011-06-24
Thanks for the info.
I cannot copy the wallpaper to XFE4/backdrops folder.
But I have copied the wallpaper (only one) to my pictures folder.
Since then I have found this addon in software centre: 
Nautilus extension. Add a "set as wallpaper" entry in context menu. and I think that has solved my problem.
I will know for sure when I next re-boot.

---

