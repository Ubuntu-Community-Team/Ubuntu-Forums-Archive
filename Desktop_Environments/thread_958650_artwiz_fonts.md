---
title: "artwiz fonts"
date: 2008-10-25
forum: Desktop Environments
---

### Post by shrndegruv on 2008-10-25
hi,  i installed the artwiz fonts following

[http://urukrama.wordpress.com/2008/05/25/artwiz-fonts-on-ubuntu-hardy/](http://urukrama.wordpress.com/2008/05/25/artwiz-fonts-on-ubuntu-hardy/)

i can use them in conky

```

use_xft yes
font snap-7

```

but cant see them in any font selection dialog under gnome.  any idea how i can fix this?

---

### Post by urukrama on 2008-10-25
Try running these commands again:

> sudo dpkg-reconfigure fontconfig
sudo dpkg-reconfigure fontconfig-config

Does that help?

---

### Post by shrndegruv on 2008-10-25
yes -- i messed up and only ran the second the first time.  it works like a chmap now.  man those are nice looking fonts.  wish i could specify a size....

---

### Post by urukrama on 2008-10-25
I'm glad you got them properly installed and working.

---

