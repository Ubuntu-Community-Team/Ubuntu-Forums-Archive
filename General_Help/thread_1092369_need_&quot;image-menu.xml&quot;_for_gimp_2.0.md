---
title: "need &quot;image-menu.xml&quot; for gimp 2.0"
date: 2009-03-10
forum: General Help
---

### Post by Shpongle on 2009-03-10
mine some how got corrupted and was removed and i get the following error

There was an error parsing the menu definition from image-menu.xml: Failed to open file '/usr/share/gimp/2.0/menus/image-menu.xml': No such file or 
directory


iv made the directory but i the file is not on my disk any where, so if someone could post the xml file up or point me in the right direction to get it
id be grateful

thanks

---

### Post by Shpongle on 2009-03-10
bump

---

### Post by Shpongle on 2009-03-11
has any1 got the file?

---

### Post by dzark on 2009-03-11
have attached

it lives in /usr/share/gimp/2.0/menus

wont let me attach as .xml file, so i've added .txt to the end, so you'll have to rename it before you use it

---

### Post by Shpongle on 2009-03-11
thanks man  , but the attachment isnt showing??

---

### Post by dzark on 2009-03-11
eek. sorry i missed the 'your attachment is too big for this file type' error message.. so same deal again, its not actually a .svg, ive just added that on to make it upload

---

### Post by geirha on 2009-03-11
Try
```
sudo aptitude reinstall gimp-data
```

---

### Post by Shpongle on 2009-03-11
thanks lads, it turned out i was missing lots of files bt that  code fixed it 



thanks again

---

