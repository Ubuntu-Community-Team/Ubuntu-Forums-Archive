---
title: "gnome-tweaks not seeing subfolder contents for options"
date: 2022-07-14
forum: Desktop Environments
---

### Post by gangliaghost on 2022-07-14
Using gnome-tweaks on Ubuntu 22.04, have installed papirus icons default folder and yellow folder icons in ~/.icons. These folders contain different subfolders containing the .theme files. gnome-tweaks does not see the .theme files in the subfolders, only the main .icon directory; in the past, I've fixed this by moving all files needed into the main .icon page, but if I install multiple themes, this can get messy. Is there a way to have gnome-tweaks find the subfolders in its drop down menu, or do I have to continue moving the files out of their subfolders? Thank you!

---

### Post by tea for one on 2022-07-15
> **gangliaghost said:**
>  Is there a way to have gnome-tweaks find the subfolders in its drop down menu
Gnome-tweaks cannot navigate into subfolders.
> but if I install multiple themes, this can get messy
I do not understand why this would be messy. Ubuntu 22.04 already has more than 20 Yaru theme options?
```
These folders contain different subfolders containing the .theme files
```
The Papirus icon folders do not have [COLOR="#FF0000"].theme[/COLOR], they have [COLOR="#0000FF"]icon-theme.cache[/COLOR] and [COLOR="#0000FF"]index.theme[/COLOR], so I can't follow what you mean?

Icon themes generally do not contain GTK themes within an Icon pack.
Changing Folder Colour in Papirus is selected via a terminal command.
[https://github.com/PapirusDevelopmentTeam/papirus-folders](https://github.com/PapirusDevelopmentTeam/papirus-folders)

---

### Post by Frogs Hair on 2022-07-21
May not apply to gnome tweaks, but is possible to have the latest papirus icons and change the folder color using the papirus folders project with commands. 

[https://github.com/PapirusDevelopmentTeam/papirus-icon-theme](https://github.com/PapirusDevelopmentTeam/papirus-icon-theme)


[https://github.com/PapirusDevelopmentTeam/papirus-folders](https://github.com/PapirusDevelopmentTeam/papirus-folders)

---

### Post by Dennis N on 2022-07-22
If your goal is to have different color folders of Papirus icon theme selectable from Tweaks, I set it up like this:

```
dmn@Tyana icons]$ ls -l 
total 36
drwxr-xr-x  8 dmn dmn 4096 Mar  8 20:41 papirus-brown
lrwxrwxrwx  1 dmn dmn   26 Jul 22 05:41 Papirus-Brown -> papirus-brown/Papirus
lrwxrwxrwx  1 dmn dmn   26 Jul 22 05:41 Papirus-Brown-Dark -> papirus-brown/Papirus-Dark
lrwxrwxrwx  1 dmn dmn   20 Jul 22 05:30 Papirus-Grey -> papirus-grey/Papirus
lrwxrwxrwx  1 dmn dmn   25 Jul 22 05:32 Papirus-Grey-Dark -> papirus-grey/Papirus-Dark
drwxr-xr-x  7 dmn dmn 4096 Jul 22 05:27 papirus-grey

```
First, create folders "papirus-brown" and "parirus-grey" 

papirus-brown: contains extracted files from papirus-icon-theme-brown-folders.tar.xz
papirus-grey: contains extracted files from papirus-icon-theme-grey-folders.tar.xz

Second, I created symlinks for each color as shown (separate links for Dark and Normal styles)

Papirus color folder themes are now separately selectable from Tweaks as Papirus-Brown, Papirus-Brown-Dark, etc.

---

