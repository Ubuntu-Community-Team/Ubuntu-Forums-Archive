---
title: "Changing Default File manager from Thunar to Konqueror"
date: 2008-04-06
forum: Desktop Environments
---

### Post by Ninjao on 2008-04-06
Hi!

I recently got myself an EEE PC and installed eeexubuntu on it. Everything is running great I have no problems. However I do prefer konqueror, and I would like to make that my default file manager.

How do I go about removing Thunar and Making Konqueror my default?

I found that tutorial blog site where the guy gives a couple of scripts for switching from Nautilus to Konqueror etc. However there are none for switching from Thunar to Konqueror. :(

p.s. I have already downloaded konqueror and launched it from terminal(i need to use it to copy something from windows) but it is not my default.

Any help is greatly appreciated!

-Julien

---

### Post by x1a4 on 2008-04-12
Hi,

Open a terminal then get yourself root priviledges like so
```
sudo -s
```

Remove the /usr/bin/thunar symlink which points to /usr/bin/Thunar 
```
rm /usr/bin/thunar
```

Recreate the symlink but point it to konqueror
```
ln -s /usr/bin/konqueror /usr/bin/thunar
```

Now Konqueror is your default file manager.  To use Thunar run /usr/bin/Thunar.  Don't remove it as it is a part of Xubuntu.

---

