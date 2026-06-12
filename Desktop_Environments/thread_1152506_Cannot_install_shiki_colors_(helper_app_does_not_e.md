---
title: "Cannot install shiki colors (helper app does not exist)"
date: 2009-05-07
forum: Desktop Environments
---

### Post by Morty007 on 2009-05-07
I get this error:

/tmp/shiki-colors-3.9.tar-1.gz could not be opened, because the associated helper application does not exist. Change the association in your preferences.


The page is here [http://www.gnome-look.org/content/show.php/Shiki-Colors?content=86717](http://www.gnome-look.org/content/show.php/Shiki-Colors?content=86717)



Can anyone help? Thanks.

---

### Post by rainwalker on 2009-05-07
I've had this error randomly other times with Firefox automatically doing things, but I haven't figured out what causes it or what fixes it (it seems to be random)

---

### Post by Kareeser on 2009-05-07
Navigate to where you downloaded the file... in your case, /tmp

Untar and unzip it with this command:
tar -xzvf shiki-colors-3.9.tar-1.gz

Place themes in /usr/share/themes
Place icons in /usr/share/icons (if you downloaded those too)

---

