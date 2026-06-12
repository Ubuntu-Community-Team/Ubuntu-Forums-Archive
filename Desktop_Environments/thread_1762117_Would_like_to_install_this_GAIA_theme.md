---
title: "Would like to install this GAIA theme"
date: 2011-05-18
forum: Desktop Environments
---

### Post by Jonauterrr on 2011-05-18
I tried Googling the answer. I tried the whole creating the ~themes folder and that didn't work. How else can I install this on Xubuntu? [http://customize.org/gtk/themes/52293](http://customize.org/gtk/themes/52293)

---

### Post by Frogs Hair on 2011-05-18
What desktop environment are you using ? The theme is for Gnome and installs Ubuntu 11.04 .

---

### Post by Jonauterrr on 2011-05-18
> **Frogs Hair said:**
> What desktop environment are you using ? The theme is for Gnome and installs Ubuntu 11.04 .

I'm using Xubuntu 11.04 and want a GAIA theme.

---

### Post by Frogs Hair on 2011-05-18
> **Jonauterrr said:**
> I'm using Xubuntu 11.04 and want a GAIA theme.

The default desktop environment for Xubuntu seems to xfce and the theme you are trying to install is for the Gnome environment , so it won't work :(

---

### Post by Toz on 2011-05-18
Actually, it will work under xubuntu (xfce). You need to get two files:

1. The Window Manager theme:```
http://customize.org/xfce/themes/52367
```

2. The GTK2 theme:```
http://customize.org/gtk/themes/52293
```

Extract the compressed files with the command:```
tar xzvf <file>
``` where <file> is the name of the file. Copy the extracted GAIA folder to ~/.themes.

Then go to your settings and change both the Window Manager theme and Appearance style to GAIA.

---

### Post by Toz on 2011-05-18
And oh, to create the ~/.themes folder, from a terminal window, type:```
mkdir ~/.themes
```

---

### Post by Jonauterrr on 2011-05-18
[IMG]http://i55.tinypic.com/16kbb10.png[/IMG]I am getting this error when extracting into themes folder.

---

### Post by Toz on 2011-05-18
You need root access to extract into that folder. Instead, create a .themes folder off of your /home directory and extract into there.

---

### Post by Jonauterrr on 2011-05-18
> **Toz said:**
> You need root access to extract into that folder. Instead, create a .themes folder off of your /home directory and extract into there.

I just did that and the theme isn't showing up with the other ones.

---

### Post by Toz on 2011-05-18
Open a terminal window and type in:```
ls -l ~/.themes
``` Post back the results.

---

### Post by LarsKongo on 2011-05-19
You should also install the gtk2-engines-pixbuf package to be able to use that theme.
```
sudo apt-get install gtk2-engines-pixbuf
```

---

