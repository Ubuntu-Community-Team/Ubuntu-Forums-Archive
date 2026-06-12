---
title: "Installing icons from folder in 9.10"
date: 2010-01-19
forum: Desktop Environments
---

### Post by senthil196 on 2010-01-19
Hello,

I downloaded the icons pack from [http://juliensagot.com/#voodoo](http://juliensagot.com/#voodoo) and have been trying to install it with no success. It comes in zip format with just png files and ubuntu isn't able to read that.

I tried copying it to /usr/share/icons in root and it home/user/.icons with no effect. I also made the theme into .tar.gz and tried to install it that way, but it just "...isn't a valid theme back"

Can anyone help me out?

Thanks

---

### Post by SumTingWong on 2010-01-19
Those are for Mac OSX, I seriously doubt they will work with Ubuntu.

---

### Post by blackened on 2010-01-19
In order for them to work as a full-fledged theme under Ubuntu they must also include an index.theme file that specifies how the icons are to be applied. This set of icons does not have an index.theme file and thus cannot be used via the Appearances manager.

You can, however, apply the icons on an individual basis by replacing icons in an existing theme with them, or by selecting any file or folder in nautilus, go to properties, then click on the icon in upper-left corner and navigate to and apply your new icon.

---

