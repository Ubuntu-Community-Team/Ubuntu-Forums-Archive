---
title: "gconftool-2 broke desktop picture"
date: 2010-01-08
forum: Desktop Environments
---

### Post by speckman on 2010-01-08
I used this command in 9.10 (gnome):
```
gconftool-2 -t str --set /desktop/gnome/background/picture_filename filename.gif
```
I was trying to write a script to download and set my desktop picture upon login.  This has worked for me before in previous versions.  Now all I have is a blank desktop, an inability to launch the set desktop appearance panel, and a grayed out option to set pictures as the desktop picture.  Ie. I broke my desktop picture.  

How can I revert this and how can I do this right?

Thanks!

---

### Post by SalahTr on 2010-01-08
Maybe the ***file_name.gif*** location is false

---

### Post by speckman on 2010-01-12
Yup, had to put in the whole path.  Duh.  Thanks a lot!!

---

### Post by SalahTr on 2010-01-12
you're welcome

---

