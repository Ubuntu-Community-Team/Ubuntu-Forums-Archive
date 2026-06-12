---
title: "Location of wastebasket icon?"
date: 2011-10-30
forum: Desktop Environments
---

### Post by woodyg on 2011-10-30
In which directory would the wastebasket icon be located in Xubuntu?

---

### Post by gsmanners on 2011-10-30
The icon is in your icon theme (/usr/share/icons more than likely).

---

### Post by Toz on 2011-10-30
I believe the files you are looking for are called **user-trash.svg** and **user-trash-full.svg** for, as gsmanners says, your respective icon theme.

> $ locate user-trash.svg
/usr/share/icons/HighContrast/scalable/places/user-trash.svg
/usr/share/icons/Humanity/places/16/user-trash.svg
/usr/share/icons/Humanity/places/22/user-trash.svg
/usr/share/icons/Humanity/places/24/user-trash.svg
/usr/share/icons/Humanity/places/32/user-trash.svg
/usr/share/icons/Humanity/places/48/user-trash.svg
/usr/share/icons/Humanity/places/64/user-trash.svg
/usr/share/icons/Tango/scalable/places/user-trash.svg
/usr/share/icons/elementary/places/22/user-trash.svg
/usr/share/icons/elementary/places/24/user-trash.svg
/usr/share/icons/elementary/places/32/user-trash.svg
/usr/share/icons/elementary/places/48/user-trash.svg

> $ locate user-trash-full.svg
/usr/share/icons/HighContrast/scalable/status/user-trash-full.svg
/usr/share/icons/Humanity/places/16/user-trash-full.svg
/usr/share/icons/Humanity/places/22/user-trash-full.svg
/usr/share/icons/Humanity/places/24/user-trash-full.svg
/usr/share/icons/Humanity/places/32/user-trash-full.svg
/usr/share/icons/Humanity/places/48/user-trash-full.svg
/usr/share/icons/Humanity/places/64/user-trash-full.svg
/usr/share/icons/Humanity/status/24/user-trash-full.svg
/usr/share/icons/Humanity/status/48/user-trash-full.svg
/usr/share/icons/Tango/scalable/status/user-trash-full.svg
/usr/share/icons/elementary/places/48/user-trash-full.svg


---

### Post by woodyg on 2011-10-31
When searching for **user-trash.svg **I find a few such files, all in /usr/share/icons. E.g. "elementary", "Humanity" and "Tango" contain such a few... but I am using greybird... which does not even have a directory in /usr/share/icons. :confused:

---

### Post by Toz on 2011-10-31
Greybird is a  window and appearance theme, not an icon theme. Go to Settings -> Settings Manager -> Appearance -> Icons tab, and it will show you the name of your current icon theme.

---

### Post by woodyg on 2011-10-31
> **Toz said:**
> Greybird is a  window and appearance theme, not an icon theme. Go to Settings -> Settings Manager -> Appearance -> Icons tab, and it will show you the name of your current icon theme.

Ahh... you learn something new every day. :) So it was elementary dark I should be looking for... Cheers!

---

### Post by Toz on 2011-10-31
You'll notice that the elementary Dark (/usr/share/icons/elementary-mono-dark) icon theme doesn't have a trash icon in any of its directories. By viewing the index.theme file:
```
$ head /usr/share/icons/elementary-mono-dark/index.theme 
[Icon Theme]
Name=elementary Dark
Comment=Dark panel icons for elementary
[COLOR="Red"]Inherits=4.0,elementary[/COLOR]

Example=directory-x-normal

#Directory list
Directories=animations/16,animations/22,animations/24,animations/32,animations/48,animations/64,animations/128,panel/16,panel/22,panel/24,panel/32,panel/48,panel/64,panel/128

```
...you'll notice that it inherits its icons from:
> Inherits=4.0,elementary
This means that if the current icon theme doesn't have the corresponding icon, it looks at the 4.0 then elementary icon themes for the icon. The 4.0 icon theme doesn't exist so that leaves us with elementary.

From the previous search, we found:
> /usr/share/icons/elementary/places/22/user-trash.svg
/usr/share/icons/elementary/places/24/user-trash.svg
/usr/share/icons/elementary/places/32/user-trash.svg
/usr/share/icons/elementary/places/48/user-trash.svg 
...and
> /usr/share/icons/elementary/places/48/user-trash-full.svg 
...for the trash empty and trash full states.

Since the trash empty icon set includes separate icons for separate sizes ( 22,24,32,48 ), locating the correct icon file is done by going to the directory that is closest to, but less than, the current size of the panel that you are trying to add it to.

Hope this helps.

---

