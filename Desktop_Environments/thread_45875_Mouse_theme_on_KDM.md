---
title: "Mouse theme on KDM"
date: 2005-07-02
forum: Desktop Environments
---

### Post by Feanor on 2005-07-02
Is it possible to change the mouse theme on KDM?? How can I do it? I've that orrible default theme...

---

### Post by SGC on 2005-07-02
Did you try to change it from:
Control center > Peripherals > Mouse > Cursor theme

---

### Post by bahadir on 2005-07-02
[QUOTE=Feanor]Is it possible to change the mouse theme on KDM?? How can I do it? I've that orrible default theme...[/QUOTE]
Hi,

look at this [nice theme](http://kde-look.org/content/show.php?content=19506) 
and [how to install](http://kde-look.org/help/index.php?type=36)

---

### Post by t2kburl on 2005-07-02
I tried to install this because I thought it looked cool.

Errored out  "not a valid archive"

I tried both the cursor only download and the cursors + source

what, exactly are you supposed to point it to to get it to install?

---

### Post by Feanor on 2005-07-02
I've the same problem... But my original problem was not to change mouse theme on KDE but on KDM! On KDE I've Kubuntu Human Theme and I like it! But on KDM I've the default ugly black pointers and I want Kubuntu Human also on it.  :neutral:

---

### Post by Feanor on 2005-07-02
Ok I've resolved by myself! I've changed the default theme with kubuntu mouse theme with this steps:

- open with a text editor /etc/X11/cursors/core.theme
- replace Inherits=core with Inherits=kubuntu
- save the file

Now the default X cursor theme is kubuntu theme and it's disappearing any strange effect also in kde when cursors change with default (I don't know if you have these effects, I had them...)

---

### Post by t2kburl on 2005-07-02
Neat work Feanor

but I still can't install the downloaded theme from kde.org

I directed it to point to the downloaded tarball, but it says its invalid.

---

### Post by Feanor on 2005-07-02
Same problem to me... I've seen that into the archive there are several folders... I tried to untar the folders and install them separately but it doesn't work. I don't think that we must to do a tar file for each folder, I'm too lazy to try now  :razz: 

I think I try later...

---

