---
title: "How to install X11 Mouse Themes?"
date: 2005-02-17
forum: Desktop Environments
---

### Post by MetalMusicAddict on 2005-02-17
Im tryin to install X11 Mouse Themes.

I did find this but call me a noob I cant find ".Xdefaults" for the life of me.

[B]Installation (Gnome and others):
---
1. Unzip the file and move the folder "whitelarge" to ~/.icons/
2. add the following two lines to your ~/.Xdefaults
##
Xcursor.theme: whitelarge
Xcursor.size: 32
##
3. log off[/B]

Taken from [THIS](http://www.gnome-look.org/content/show.php?content=19902&forummode=2&forumpage=0&forumexplevel=0) page.
 
And does ~/ mean your home directory?

"locate .Xdefaults" didnt find the file even after i ran "sudo updatedb"

---

### Post by MetalMusicAddict on 2005-02-18
I did find out about gcursor but I cant find it in apt. I saw its supposed to be in "Universe".

---

### Post by Perfect Storm on 2005-02-18
It's not in the universe or multiverse.(warty)

You can get it here: [http://qballcow.nl/?name=gcursor&css=0](http://qballcow.nl/?name=gcursor&css=0)

You need to compile it.

---

### Post by MetalMusicAddict on 2005-02-18
Ahh. Thanx sir. ;)

---

### Post by Stefan_hb on 2005-02-28
Hi,
I'm the author of the "whitelarge" theme. Since I switched to ubuntu, too, I had the same problem. You can install it this way.

1. Unzip the file and move the folder "whitelarge" to ~/.icons/
2. open the gconf editor
3. change the key
/desktop/gnome/peripherals/mouse/cursor_theme
to "whitelarge"
4. log off

My mouse themes:
[http://www.go77.de](http://www.go77.de)

---

### Post by MetalMusicAddict on 2005-02-28
Awesome man. Thanx. :) Your cursors are cool man.

---

