---
title: "nautilus scripts - convert to jpg, and icon size problem"
date: 2005-10-24
forum: Desktop Environments
---

### Post by jamesford on 2005-10-24
hi, firstly i was wondering how to get a nautilus script that converts any image (most importantly png) to jpg. ive tried the scipt that comes in the nautilus-scripts.tar.gz here [http://g-scripts.sourceforge.net/index.php](http://g-scripts.sourceforge.net/index.php) but for some reason it isnt doing anything. the  script looks like
-----
#!/bin/bash

while [ $# -gt 0 ]; do
	picture=$1
	jpg_file=`echo "$picture" | sed 's/\.\w*$/.jpg/'`
	/usr/bin/convert -quality 75 "$picture" jpeg:"$jpg_file"
	shift
done
------
how can i make it work ? are there any packages i need to install ? (yes they are +x)

secondly i have a problem with the icon size in the scripts menu. ive chosen my own icons for most of the scripts, the problem is that if i chose icons size 48x48 the icons in the menu are huge ( see [http://img149.imageshack.us/img149/8236/icons4xi.jpg](http://img149.imageshack.us/img149/8236/icons4xi.jpg) )

and if i chose icons smaller than 48x48 all the icons in the menu become tiiiiny. is there a way to make them normal size, like all the other icons in the rightclick menu ?

thank you

---

### Post by fog on 2005-10-25
You must install **imagemagick**.

---

