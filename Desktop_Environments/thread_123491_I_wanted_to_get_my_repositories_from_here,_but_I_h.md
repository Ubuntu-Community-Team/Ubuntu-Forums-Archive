---
title: "I wanted to get my repositories from here, but I have no idea how..."
date: 2006-01-30
forum: Desktop Environments
---

### Post by Mykas0 on 2006-01-30
I've just installed the latest version from the CD, and now when the OS is loading it features an "ubuntu" image on the background, a completion bar and some text appearing below.
However, I really dislike this, I'd rather have the old text one, is there any way to get that one?

---

### Post by jasmuz on 2006-01-30
sudo apt-get remove usplash

---

### Post by aysiu on 2006-01-30
Another way to do it is ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
``` and then take out the word *splash* from the kernel line of your Ubuntu entry.

---

