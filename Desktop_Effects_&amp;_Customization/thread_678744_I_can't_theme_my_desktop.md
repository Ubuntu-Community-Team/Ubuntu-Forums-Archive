---
title: "I can't theme my desktop"
date: 2008-01-26
forum: Desktop Effects &amp; Customization
---

### Post by krisim on 2008-01-26
I don't know if I'm doing something wrong but, when i try to install a theme in the appearance manager, nothing happens. I've also tried to drag and drop the theme in there. 

Is there a solution or am I just doing it wrong?

---

### Post by wookietim on 2008-01-26
Bump

---

### Post by Tenken on 2008-01-26
What type of theme are you trying to install (icons,metacity,emerald,etc)? And are you getting any error messages when you try to install them?

---

### Post by PCWizKid on 2008-01-26
Man, I feel your pain brother, I got some info on themes here if your interested.

[http://pcwizkid.blogspot.com/2007/12/ubuntu-gutsy-gibbon-710-vs-osx-leopard.html](http://pcwizkid.blogspot.com/2007/12/ubuntu-gutsy-gibbon-710-vs-osx-leopard.html)


Cheers
PCwizKid

---

### Post by krisim on 2008-01-27
Oh some of it works, which is pretty weird since I've been doing the same thing over and over again. There's something that i can't get to work though, I'm trying to install the "Aurora Gtk Engine" from gnome-looks. I start to extract the file I've downloaded "56438-Aurora-1.4.tar.bz2", and get "aurora-1.4.tar.gz" and "gtkrc_themes.tar.bz2" out of it. I then try to install both of them in the appearance manager, "gtkrc_themes.tar.bz2" installs nicely and says there has been 3 themes installed, but "aurora-1.4.tar.gz" won't install and says; "This is a theme engine. It has to be compiled." (Excuse the translation, I'm using Danish in Ubuntu"

Well how do i compile it, and is that really what I'm supposed to do?

---

### Post by GavinZac on 2008-01-27
from the instructions:

To install the theme engine extract it to somewhere convenient and in that directory, these commands run: 

./configure --prefix=/usr -enable-animation
make
sudo make install

(you've done this bit...) Then install the gtkrc themes by extracting them to your ~/.themes directory (3 themes in total).

---

