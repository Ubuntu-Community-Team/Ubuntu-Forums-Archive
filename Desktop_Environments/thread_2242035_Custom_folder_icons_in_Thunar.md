---
title: "Custom folder icons in Thunar"
date: 2014-08-30
forum: Desktop Environments
---

### Post by michael_sund2 on 2014-08-30
I searched to find information on how to change icons (not emblems) for specific folders in Thunar, to my surprise all I found was 2 years old bugtracker entries. So, now it's 2014, has it been added yet? I can't imagine it'd be that big a project to implement custom folder icons...

If it's not possible, would you recommend an alternative file manager?

---

### Post by vasa1 on 2014-08-30
Well, if you find it easy please come up with something. Not just for Thunar but also for PCManFM. That would be much appreciated.

---

### Post by Rob Sayer on 2014-08-30
I've never done this myself but I think Dolphin will do it.  That's the file manager I use on any linux DE.  And I particularly dislike Thunar and PCmanfm.  Installing dolphin will also install a ton of KDE dependencies but that's not been a problem for me.  Though you'd want to be careful with autoclean ...

It's not magic that the DEs like xfce and lxde are so much lighter.  They lack features.  At some point that slows me up, so I use a powerful file manager.

---

### Post by michael_sund2 on 2014-08-30
> **vasa1 said:**
> Well, if you find it easy please come up with something. Not just for Thunar but also for PCManFM. That would be much appreciated.
I just meant that they already support folder icons (like Pictures, Downloads, Music, Video etc), just not changing them. I just thought that it wouldn't be a problem for those who actually created the program.

> **Rob Sayer said:**
> I've never done this myself but I think Dolphin will do it.  That's the file manager I use on any linux DE.  And I particularly dislike Thunar and PCmanfm.  Installing dolphin will also install a ton of KDE dependencies but that's not been a problem for me.  Though you'd want to be careful with autoclean ...

It's not magic that the DEs like xfce and lxde are so much lighter.  They lack features.  At some point that slows me up, so I use a powerful file manager.
Hm, I'll check Dolphin out. :)

EDIT: Changed my mind, I really want to keep Thunar, but it'd be nice if I could make my own plugins for it. I found a page with like 6 plugins for it, but no documentation on how to develop them. Is is possible to create Thunar plugins?

EDIT2: Found documentation for development.

---

### Post by vasa1 on 2014-08-30
I think Nautilus and Nemo are two other file manager that have this facility but using a file manager that isn't the default may see the new file manager trying to take over management of the desktop as well. Which is why I would recommend caution while changing file managers.

---

### Post by Toz on 2014-08-30
> **michael_sund2 said:**
> I just meant that they already support folder icons (like Pictures, Downloads, Music, Video etc), just not changing them. I just thought that it wouldn't be a problem for those who actually created the program.

If you're willing to roll up your sleeves, you can change those icons yourself (the hard way) using the freedesktop icon spec. Basically, you would create a new icon theme based on your current theme, have that icon theme inherit your current theme, and create the icons that you want to use to override the existing ones. Here is an example of how to override the icons for the Faenza theme:

1. Create a new theme in your ~/.icons folder (create the folder if it doesn't exist):
```
mkdir -p ~/.icons/MyTheme/places/scalable
mkdir -p ~/.icons/MyTheme/places/48
mkdir -p ~/.icons/MyTheme/places/32
mkdir -p ~/.icons/MyTheme/places/24
mkdir -p ~/.icons/MyTheme/places/22
mkdir -p ~/.icons/MyTheme/places/16
```

2. Copy your current icon theme's index.theme file to your new location:
```
cp /usr/share/icons/Faenza/index.theme ~/.icons/MyTheme/
```

3. Edit the index.theme file that you just copied over. Change the Name and comment fields to your liking and change the "Inherits=" field to point to your current icon theme. Leave the rest of the file as is. Here is what the top of the file would look like:
```

[Icon Theme]
Name=MyTheme
Inherits=Faenza
Comment=Icon theme overrides
```

4. Now to replace the icons, you need to create replacement icons and put them in the panels/scalable (svg) and places/16 (png), places/22 (png), places/24 (png), places/32 (png), places/48 (png) directories. I suggest you start with and svg version of the file that you want and put it in the scalable directory. Then use gimp to import the svg and scale it to the appropriate sizes (48x48, 32x32, 24x24, 22x22, 16x16) one at a time, and export them to the appropriate directories. _Note:_ the names for those icons need to be:
- home directory = user-home
- Music = folder-music
- Documents = folder-documents
...to determine the folder name to be used, run the following command:
```
gvfs-info ~/Music | grep "standard::icon"
```
...change the path as required, and use the first folder name returned. For example:
```
$ gvfs-info ~/Documents | grep "standard::icon"
  standard::icon: folder-documents, folder
```
...you would use "folder-documents".

5. When all the above is done, change your icon theme (Settings Manager >> Appearance >> Icons) to your new theme.

For reference, here is what the new theme folder/file structure looks like after the Music folder icon was overridden:
> 
/home/toz/.icons/MyTheme/
/home/toz/.icons/MyTheme/index.theme
/home/toz/.icons/MyTheme/places
/home/toz/.icons/MyTheme/places/32
/home/toz/.icons/MyTheme/places/32/folder-music.png
/home/toz/.icons/MyTheme/places/scalable
/home/toz/.icons/MyTheme/places/scalable/folder-music.svg
/home/toz/.icons/MyTheme/places/22
/home/toz/.icons/MyTheme/places/22/folder-music.png
/home/toz/.icons/MyTheme/places/16
/home/toz/.icons/MyTheme/places/16/folder-music.png
/home/toz/.icons/MyTheme/places/24
/home/toz/.icons/MyTheme/places/24/folder-music.png
/home/toz/.icons/MyTheme/places/48
/home/toz/.icons/MyTheme/places/48/folder-music.png


---

### Post by vasa1 on 2014-08-30
@Toz, I think what OP wants is to customize the appearance of *any* folder, not just the "special" ones: Home, Desktop, Music, Documents, Public, Templates, Pictures, Downloads, etc.

This can be done in Nautilus (and Nemo): 
[http://www.webupd8.org/2014/04/folder-color-easily-change-folder-icon.html](http://www.webupd8.org/2014/04/folder-color-easily-change-folder-icon.html)
[http://www.webupd8.org/2014/08/nemo-emblems-folder-color-image.html](http://www.webupd8.org/2014/08/nemo-emblems-folder-color-image.html)

It can also be done in MS Windows.

---

