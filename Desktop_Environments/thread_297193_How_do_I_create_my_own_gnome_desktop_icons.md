---
title: "How do I create my own gnome desktop icons?"
date: 2006-11-10
forum: Desktop Environments
---

### Post by amanda on 2006-11-10
I am addicted to the pretty, pretty Marmalade Moon icons:
[http://www.marmalademoon.com/](http://www.marmalademoon.com/)

but I don't know how to use them on Ubuntu. I'm running Breezy, but I doubt that makes any difference. The Windows sets are just .ico files that I can preview, but I don't know what format to save them in to make them accessible as icons for Gnome.

The Mac sets don't have file extensions (ahh mac, love those file extensions), so my guess is that the Windows ".ico" files are what I need to use. What format should I save them in to be able to use them with gnome?

(Actually, this might be a more advanced question than I thought. I used convert to make them into .pngs, and got 8 images, one of each layer. So what format will accept all the layers in these .ico files?)

---

### Post by BLTicklemonster on 2006-11-10
Wellll, you need permission to use them I guess. Do they come in individual images, of 4 to a picture? 

You can use Gimp to save them to .png format, and save them in your /home/amanda folder (even make an icon folder if you want), then choose one of them as your icon.

[http://ubuntuforums.org/showthread.php?t=92393](http://ubuntuforums.org/showthread.php?t=92393)

for a how to.

the pictures I had on there are long gone, my ftp site is non-existant...

---

### Post by CatKiller on 2006-11-10
> **amanda said:**
> (Actually, this might be a more advanced question than I thought. I used convert to make them into .pngs, and got 8 images, one of each layer. So what format will accept all the layers in these .ico files?)

You probably don't want a format that has them all clumped together again. If you look at an existing Gnome icon theme (there are some stored in **/usr/share/icons**) you'll see that they are made of variations of the icons at different sizes (**16x16**, **32x32**, **48x48** and so on), and a **scalable** directory for SVG images.

[This]("http://live.gnome.org/GnomeArt/Tutorials/IconThemes") is a fairly official-looking tutorial on how to make an icon theme for Gnome. And you can download plenty of others from there to look at, too.

BLTicklemonster is right though - you'll have to get permission before you're allowed to share them with anyone.

---

### Post by slavik on 2006-11-10
Steps to make icons for GNOME:

1. Open GIMP (or any other image editing/creating program)
2. Draw the icon
3. Save
4. ???
5. Profit!

Really, just draw what you want as an icon and save it ... check out the tutorial in CatKiller's post for a way to actually package them in a convenient manner.

---

### Post by amanda on 2006-11-12
> **BLTicklemonster said:**
> Wellll, you need permission to use them I guess. 

Oh dear. I guess I am more selfish than you were expecting. I didn't want to create desktop icons to share with, um, other people. I just wanted to use Marmalade Moon's icons for me.

---

### Post by amanda on 2006-11-12
This blog post: [http://arstechnica.com/articles/columns/linux/linux-20040429.ars](http://arstechnica.com/articles/columns/linux/linux-20040429.ars)

Looks like it is a lead on what I want (scroll down to "Tools, Tips and Tweaks") but the site they link to for icons2png has been squatted. 

Seems like opening the .ico files in documentviewer and then saving them as .png is the quickest way to get desktop icons, but I'm tinkering with the arstechnica directions.

---

