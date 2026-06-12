---
title: "Font problem when running some apps.."
date: 2005-12-13
forum: Desktop Environments
---

### Post by BathroomNinja on 2005-12-13
I've already used Automatix.
Almost everything has perfect fonts, except for some things like:

DVDrip or in this example, America's Army installer.

Here is a screen capture, I put up a few 'working' apps so you can see the difference. 

Anyone know of a way to fix this so it's readable?

---

### Post by BathroomNinja on 2005-12-14
Anyone elese having this problem?

---

### Post by BathroomNinja on 2005-12-16
I think I may be able to fix this by  creating a symlink:
 /usr/X11R6/lib/X11/fonts/ -> /usr/share/X11/fonts/

I will try this when I get home and report.

---

### Post by brj on 2005-12-16
i had the same problem and i could fix it by declaring the font in 
.gtkrc.mine in the home directory.

```

style "user-font"
{
  fontset="-adobe-helvetica-medium-r-normal-*-80-*-*-*-p-*-iso8859-1"
}

widget_class "*" style "user-font"

```

the file .gtkrc.mine is referenced by .gtkrc-1.2-gnome2.

you can use gtkfontsel to construct the fontstring for fontset=

jakob

---

### Post by BathroomNinja on 2005-12-16
That worked, thanks brj
ok, I did this from the terminal.  Make sure you are in your home directory.

$sudo apt-get install gtkfontsel
$sudo gedit .gtkrc.mine

paste the following:```

style "user-font"
{
  fontset="-adobe-helvetica-medium-r-normal-*-80-*-*-*-p-*-iso8859-1"
}

widget_class "*" style "user-font"

```

Save and close.
logout, log back in.  


FIXED

---

