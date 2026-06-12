---
title: "XFCE-Stellar Theme"
date: 2009-04-15
forum: Desktop Environments
---

### Post by Scabby_al on 2009-04-15
I love the look and feel of the XFCE-Stellar theme but I want to change the selected items color from pink to blue. I have gnome-color-chooser and I've scoured the interwebs and haven't found a solution or a way to customise the color.

---

### Post by denham2010 on 2009-04-15
To do this, you need to edit the gtkrc file for the theme.

Sounds more difficult than it is.

Open a terminal end enter the following commands:

```
mkdir ~/.themes/Stellar-Mod
```
```
cp -r /usr/share/themes/Xfce-stellar/* ~/.themes/Stellar-Mod/
```
```
gedit ~/.themes/Stellar-Mod/gtk-2.0/gtkrc
```

This creates a copy of the Stellar theme under a different name so you can make changes and experiment without affecting the original.

Now you will have the theme file open in a text editor.

For your specific question, changing the pink to blue, locate the lines (45 & 47)
```
base[SELECTED] = "#b24d7a"
base[PRELIGHT] = "#b24d7a"
```

These are the 'pink' colour you want to change. Just change the colour to the blue you want and save the file.

If you are not familiar with hex colours, open a program like Gimp or Gnome-Color-Chooser and select a colour you like. It will show you the hex number to use.

Now that is done, open up your theme selector and there should be a new entry called 'Stellar-Mod' for you to select.

Cheers.

---

### Post by Scabby_al on 2009-04-15
Thanks for the help! Much appreciated!

---

