---
title: "Fedora Fonts Are diferent"
date: 2005-12-14
forum: Desktop Environments
---

### Post by nurv on 2005-12-14
Hi there!

I notice that fedora's gnome standart fonts are different. I don't know if is the rendering engine or if they mashup fonts. I like them more than the ubuntu standart.

I have another computer with fedora and i tried to download their fonts to my ubuntu but they are the same.

compare your gnome terminal with this

[http://www.dark-hill.co.uk/fedora/screenshot-9.html]("http://www.dark-hill.co.uk/fedora/screenshot-9.html")

Does any one knows what causes this?

---

### Post by 23meg on 2005-12-15
It probably has to do with the antialiasing method in use. Play with the hinting settings in System / Preferences / Font and also check out [this thread]("http://www.ubuntuforums.org/showthread.php?t=20976") for some more info.

---

### Post by nurv on 2005-12-15
Got It!!! 

just install t1-xfree86-nonfree, ttf-xfree86-nonfree, etc... Simply install all packages of xfree86-nonfree and change every sans to Luxi sans and Monospace to Luxi Mono! Don't forget change gnome-terminal!

And also change firefox fonts! Digg, for instace, looks better!

This fonts are WAY better than bit vera fonts! I Hope that ubuntu folks could put this as standart, but licence agreements...

---

### Post by 23meg on 2005-12-15
You could also try doing ```
sudo dpkg-reconfigure fontconfig
``` and try  enabling the autohinter module there.

---

