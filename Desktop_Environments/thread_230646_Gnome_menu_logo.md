---
title: "Gnome menu logo"
date: 2006-08-06
forum: Desktop Environments
---

### Post by Big_J on 2006-08-06
I've been trying to change the Ubuntu logo next to the applications menu into the gnome foot for about half an hour now, yet no luck.
I was pretty sure that the logo is associated with /usr/share/pixmaps/gnome-logo-icon-transparent.png, but that one is infact a foot!

When I try to use the configuration editor, I get an error message saying that it can't find the picture I specify, even though I draged the image in so I know there's no missing letters. 

So in short, how exactly do you change the logo in Ubuntu (6.06)??

---

### Post by tseliot on 2006-08-06
moved to a more appropriate section

---

### Post by BIGtrouble77 on 2006-08-06
The easiest way is to setup a profile with custom icons.  So in your /home/name/.icons directory copy your icon theme there.  You can get one off of gnome-look.com or just copy one of the default system icon themes there.

Now I think you have to go into the 48x48/places and find the start-here.png (I don't know which of the different size sections takes prescedence).  Replace that icon with the gnome foot.  Within the directory you'll also have to create a link to that file called distributer-logo.png.  You can find the foot icon in /usr/share/pixmaps.  If you use a large svg icon, larger than 48x48, it might scale your panel which you definately don't want.  If you do it right the ubuntu logo will be replaced every time.

Some of the other howto's here that try to solve this problem are simply wrong.  This will work every time if you do it correctly.  If you have issues I can give you more detailed instructions.

---

### Post by Tsukasa on 2006-08-06
You have to modify distributor-logo.png.

Be sure to edit the file for your current iconset, which you can usually find under ~/.icons/

---

### Post by m83 on 2006-08-06
See my solution [from here]("http://ubuntuforums.org/showthread.php?t=208457&page=2").

---

