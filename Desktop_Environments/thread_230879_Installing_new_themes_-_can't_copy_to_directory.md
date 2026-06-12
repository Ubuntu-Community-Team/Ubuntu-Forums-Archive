---
title: "Installing new themes - can't copy to directory"
date: 2006-08-06
forum: Desktop Environments
---

### Post by kvalis on 2006-08-06
Downloaded the theme **T-ish-Brushed-Aquastyle** from Gnome Kook-org's website.
Found out how to extract and how to copy the theme to the usr/share/themes directory, but no luck. Here is the command I issued:

> root@ubuntu:/home/tore# ls
Desktop                  automatix-installer    jriddell.key       quinn2.key
Readme.htm               automatix.log          key.gpg.asc
Readme.txt               flashplayer-installer  libflashplayer.so
T-ish-Brushed-Aquastyle  flashplayer.xpt        quinn1.key
root@ubuntu:/home/tore# cp /T-ish-Brushed-Aquastyle/ /usr/share/themes
cp: cannot stat `/T-ish-Brushed-Aquastyle/': No such file or directory
root@ubuntu:/home/tore#


Can you explain if I have looked at the wrong command??


Kvalis

---

### Post by linuxgeekery on 2006-08-06
There's a better way to install themes. :)

Just go to System > Preferences > Theme and drag and drop the theme tarball (not the folder) onto the Theme window. That's it!

---

### Post by kvalis on 2006-08-06
Thanks linuxgeekery.

That was easy enough.

Brilliant

Kvalis

---

### Post by bulldog on 2006-08-06
And if you want to cp the file,be sure that you are in the folder where the file is.
For instance,when the file is on your Desktop you have to do cd /Desktop before you can copy the file.

---

