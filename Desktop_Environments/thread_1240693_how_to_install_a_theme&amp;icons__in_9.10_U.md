---
title: "how to install a theme&amp;icons  in 9.10 U"
date: 2009-08-15
forum: Desktop Environments
---

### Post by samuraitor on 2009-08-15
hey,

how do I go about installing a new theme &icons in ubuntu 9.10?Below is the link to the website from where I got the files but uncertain about the installation.

[http://osliner.deviantart.com/art/Ubuntu-Brawnee-Look-71752672]("http://osliner.deviantart.com/art/Ubuntu-Brawnee-Look-71752672")

I got a folder for icons and a folder for theme with a gtk file.

---

### Post by warp99 on 2009-08-15
Right mouse click on an empty space on your desktop then choose "Change Desktop Background". When the background dialog opens choose the theme tab. In the right lower corner there's a button that says install. Click on that and browse to the file you just download.

---

### Post by samuraitor on 2009-08-15
> **warp99 said:**
> Right mouse click on an empty space on your desktop then choose "Change Desktop Background". When the background dialog opens choose the theme tab. In the right lower corner there's a button that says install. Click on that and browse to the file you just download.

unfortunately, not installable ... what about te icons?

---

### Post by warp99 on 2009-08-15
I download the theme files and they don't include an install file so you have to copy them manually into the /usr/share/theme directory. So here's how I did it:

First extract the tar file:
```
tar -xvf 837a4a24f8b2c6ee.gz
```

Then copy the theme folder into the theme directory:
```
cd brawnee
sudo cp -r themes /usr/share
```

Now the theme will show up in your theme dialog, but the icons will be missing.

To copy the icons do the following:
```
sudo mkdir /usr/share/icons/brawnee
```

Then copy the icons and the index.theme file:
```
sudo cp -r icons/* /usr/share/icons/brawnee
```

---

