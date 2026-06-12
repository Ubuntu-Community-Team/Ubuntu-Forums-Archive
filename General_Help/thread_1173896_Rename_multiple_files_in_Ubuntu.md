---
title: "Rename multiple files in Ubuntu"
date: 2009-05-30
forum: General Help
---

### Post by chmacka on 2009-05-30
Is there a way to rename multiple files in Ubuntu (v 9.04)?

For example, if I have

qwoir.jpg
sjaflkajl.jpg
oqpriu90qwr.jpg

can I rename them to:

Blah (1).jpg
Blah (2).jpg
Blah (3).jpg.

In windows (at least XP) this is accomplished by selecting all files you want to rename and pressing F2. You type the name for the first file and all the other files get the numbers [(1), (2), (3) ...] - [HOW TO: Rename Multiple Files in Windows XP with Windows Explorer]("http://support.microsoft.com/kb/320167").

---

### Post by AllanPoe on 2009-05-30
You could try a nautilus script called Renamer: [http://gnome-look.org/content/show.php/Renamer?content=87601](http://gnome-look.org/content/show.php/Renamer?content=87601)

---

### Post by _Purple_ on 2009-05-30
You can install krename if you are looking for an application with GUI.

```
sudo apt-get install krename
```

Then run it from terminal using
```
krename
``` 

If you are looking for a CLI application, you can try renrot.
```
sudo apt-get install renrot
```

---

### Post by colau on 2009-05-30
[http://wareseeker.com/free-multiple-rename-linux/](http://wareseeker.com/free-multiple-rename-linux/)

---

### Post by chmacka on 2009-05-30
Thank you all!

I decided to use krename - it seams like the easiest way. :D

---

### Post by 73ckn797 on 2009-05-30
Thunar also has a simple renaming capability integrated in the file manager.

---

