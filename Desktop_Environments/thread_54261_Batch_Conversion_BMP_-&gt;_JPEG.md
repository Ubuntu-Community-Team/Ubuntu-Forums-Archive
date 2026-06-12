---
title: "Batch Conversion BMP -&gt; JPEG"
date: 2005-08-04
forum: Desktop Environments
---

### Post by sinbad782 on 2005-08-04
Hi,
  I need to convert about fifty or so similar sized bitmaps into jpeg images (these are desktop wallpapers). Does anyone know of a good tool (or an easy method using the standard tools) to do this all in one go?

Thanks,

PJS

---

### Post by Fed7 on 2005-08-04
[QUOTE=sinbad782]Hi,
  I need to convert about fifty or so similar sized bitmaps into jpeg images (these are desktop wallpapers). Does anyone know of a good tool (or an easy method using the standard tools) to do this all in one go?

Thanks,

PJS[/QUOTE]

You can try "ImageMagic".

So, install "ImageMagic", then from shell:
#convert $name.bmp $name.jpg

If you have many files, then you can write a small script. For example:

#!/bin/sh
# Scriptino di Federico Sette (C) 2004
for i in $(seq 1 9); do
convert 00$i.bmp 00$i.jpg
done
for j in $(seq 10 99); do
convert 0$j.bmp 0$j.jpg
done

Save the file as "convert.sh" and, from shell, do:
#chmod +x convert.sh

Sorry, but my english is very bad :(
By,
Fede

---

### Post by sinbad782 on 2005-08-05
Thanks - sounds like a good idea.

---

### Post by sinbad782 on 2005-08-05
This also came up on Linux.com today - some nice tricks:

[http://applications.linux.com/applications/05/03/29/1525217.shtml?tid=39&tid=49&tid=47](http://applications.linux.com/applications/05/03/29/1525217.shtml?tid=39&tid=49&tid=47)

---

### Post by eoinmadden on 2007-01-12
Handy script. Thanks, Fede.

---

