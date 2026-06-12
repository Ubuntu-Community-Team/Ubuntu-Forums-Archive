---
title: ".ico to .png conversion"
date: 2005-06-01
forum: Desktop Environments
---

### Post by mike998 on 2005-06-01
Does anyone know how to convert .ico (windows version) to .png so I can use them in Gnome?  
I can do it in Gimp manually by opening the file and deleting all but one layer and saving the resulting file as a .png, but I have several hundred files to convert, and a batch file would make things a lot easier.

---

### Post by Xerampelinae on 2005-06-01
sudo apt-get install imagemagick

This gives you the convert command.

Then from whatever directory, this would convert all the .ico files to .png files.  The basename thing strips the .ico extension off of $i (the current filename), so that you don't have image.ico.png names but rather image.png names.

for i in *.ico; do convert $i `basename $i .ico`.png; done

---

### Post by bvc on 2005-06-01
gthumb

---

### Post by mike998 on 2005-06-01
bvc's post worked.  I honestly didn't think to try saving the files once they opened in gthumb.

The one line script didn't really work.  It pulled out all the individual layers and converted them to .png, but left them grainy and not looking very nice at all.

Thanks for the help!

---

