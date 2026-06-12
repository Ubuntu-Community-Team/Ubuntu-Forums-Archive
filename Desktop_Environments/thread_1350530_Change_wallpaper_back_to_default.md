---
title: "Change wallpaper back to default"
date: 2009-12-09
forum: Desktop Environments
---

### Post by felixvah on 2009-12-09
I have Ubuntu 9.10 and messed with the wallpaper and for whatever I did I can't change the wall paper back or to any other wall paper at all.  Can someone help. 

I've create new account and still can't change the wall paper.  What I did was playing with the gconftool-2 command and I end up stuck with one wall paper.  

Here's the code I did with gconftool-2 --set /desktop/gnome/background/picture_file /home/me/Firefox_wallpaper.png

Here's the error:
Can't overwrite existing read-only value: Can't overwrite existing read-only value:
Value for `/desktop/gnome/background/picture_filename' set in a read-only
source at the front of your configuration path

If I tweak the code a bit this is what I get:
Must specify a type when setting a value

Can someone point me to the right direction or show me how to reset it back to default without have to re-install again.

thanks

---

