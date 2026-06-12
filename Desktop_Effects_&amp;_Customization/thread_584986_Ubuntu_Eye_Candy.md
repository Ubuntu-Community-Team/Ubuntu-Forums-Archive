---
title: "Ubuntu Eye Candy"
date: 2007-10-21
forum: Desktop Effects &amp; Customization
---

### Post by Mayfairy on 2007-10-21
Just like the title says I'm looking for some nice eye candy stuff for Ubuntu. 
I'm currently using Compiz-fusion, Emerald, Kiba-dock, Conky, Screenlets, Xwinwrapper (for animated wallpaper) and Yakuake. Also have tried gDesklets and AWN but ended up using the ones mentioned above. 

Are there any other such programs and tools I don't know about? Something to make my desktop work a bit smoother (like yakuake) or plain eye candy?

EDIT: Did some more forum search and trying out gnome-dock to replace kiba-dock.

---

### Post by Timsy321 on 2007-10-21
I have been trying for a few days now to get kiba-dock installed on my system. I can't seem to find a good instruction base to go off of. How did u get it installed, also i think i installed it fine, but i couldnt run it. I would type it in but it would never show up. If you could give any help that would be awesome. Thanks!

---

### Post by Mayfairy on 2007-10-21
I was running Feisty at the time of the install. 
Used Trevino's repository to install it. 

#Kiba dock
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

Used Synaptic to install everything found with 'kiba-dock' search. I think there were 5 or 6 packets. 

You need to have installed all these dependencies: 
automake1.9
cvs
Pango1.0-devel
GTK2-devel
gconf2-devel
Glitz-glx-devel
librsvg2-devel
libglade2-devel
AIGLX., XGL Beryl or AIGLX compiz.

After all these are installed just run run 'kiba-dock' from a terminal. That way you'll see possible errors.

---

