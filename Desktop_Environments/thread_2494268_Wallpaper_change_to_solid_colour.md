---
title: "Wallpaper change to solid colour"
date: 2024-01-10
forum: Desktop Environments
---

### Post by angel mike on 2024-01-10
Tryng to change wallpaper to a solid colour using Dconf Editor. 

The colour is
 Indigo Blue PMS: 3535 C
Hex Color: #4b0082;
RGB: (75,0,130)
CMYK: (42,100,0,49).

I can delete the existing  picture uri and picture uri dark values.
What do I replace them with and how do I active the change?
Using Ubuntu 22.04 with a laptop.

---

### Post by #&amp;thj^% on 2024-01-10
Something like;
```
gsettings set org.gnome.desktop.background primary-color '#4b0082'
```

---

### Post by angel mike on 2024-01-11
Thanks IFallen. Do I put that in both the Picture url and Picture url dark?

---

### Post by #&amp;thj^% on 2024-01-11
> **angel mike said:**
> Thanks IFallen. Do I put that in both the Picture url and Picture url dark?
Dang that is a good question, I just tried my suggestion and it did not work.
Seems more has to be changed from 20.04 to 22.04. 
@angel mike would it be easier to just make a background with gimp?
I've been playing with this today:
```
gsettings set org.gnome.desktop.background picture-options 'none'
gsettings set org.gnome.desktop.background primary-color '#004000'
gsettings set org.gnome.desktop.background secondary-color '#306030'
gsettings set org.gnome.desktop.background color-shading-type 'vertical'
``` 
My color is different than the one you want so heads up there.
You may have to play a bit with it like:

First, clear the background image:
```
gsettings set org.gnome.desktop.background picture-uri-dark none
```

Set the background color:
```
gsettings set org.gnome.desktop.background primary-color '#000000'
```

And to set it.
```
sudo dconf update

```
I still think the best route is to create your background with a image manipulation tool like Gimp.

---

### Post by angel mike on 2024-01-11
Thanks 1Fallen for doing all that research - much appreciated. I'll have a play around and report back..

---

### Post by #&amp;thj^% on 2024-01-11
This may help as well: [https://help.gnome.org/admin//system-admin-guide/3.12/background.html.en](https://help.gnome.org/admin//system-admin-guide/3.12/background.html.en)

---

### Post by Dennis N on 2024-01-11
The solid color option was removed years ago from Gnome. You need to make an rectangular image filled with the desired color and use that. Inkscape does this easily.

---

### Post by angel mike on 2024-01-12
I finally managed it using the Dconf Editor. Set the picture url  and the picture url dark to blank just leaving the ' '  apostrophe marks. Then then set the primary colour code to required value which in my case was '#4b0082' for Indigo blue. Then set the secondary colour code to 'ffffff' the code for a white background. 
Thanks for all the contributions

---

