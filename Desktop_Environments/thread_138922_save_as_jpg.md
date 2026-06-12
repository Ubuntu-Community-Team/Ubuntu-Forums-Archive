---
title: "save as jpg"
date: 2006-03-02
forum: Desktop Environments
---

### Post by Zain on 2006-03-02
does anyone know how i can save an image as a jpg rather than png? i cant seem to figure it out.
thanks guys

---

### Post by Mustard on 2006-03-02
Open the image in the GIMP application.

Choose 'Save As' from the File menu.

Go down to 'Select by File Extension' and select 'JPEG'

Save the file.

Screenshot below for reference.

[[IMG]http://img210.imageshack.us/img210/1664/screenshot19sl.th.png[/IMG]](http://img210.imageshack.us/my.php?image=screenshot19sl.png)

---

### Post by Spano on 2006-03-02
Don't know if this is the most elegant solution but what I would do is download the .png and convert it to .jpg in gimp.

---

### Post by Zain on 2006-03-02
ok, thanks guys!

---

### Post by engla on 2006-03-02
gThumb is a bit lighter; it's an image preview/slideshow application that can do the same thing.

Open with gThumb, then > Save as.. and name it newname.jpg, Save.

---

### Post by xmastree on 2006-03-02
There's a faster way, if you downlod image magick you can convert it with the **convert** command. Once you have that, you can make a simple nautilus scrips then right click the image and convert it.

Like this:
```
#!/bin/sh
for arg 
do
convert "$arg" -quality 85 temp.jpg
mv "temp.jpg" "`basename "$arg" .png`.jpg"
done
```

---

