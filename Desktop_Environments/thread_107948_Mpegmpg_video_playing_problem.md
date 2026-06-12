---
title: "Mpeg/mpg video playing problem"
date: 2005-12-24
forum: Desktop Environments
---

### Post by powerrangers009 on 2005-12-24
hallo
i just downloaded a "mpeg"  file but im not able to play it with totem video player.
what should i do now ?
i have really no idea what should i do because when i try to play it in "totem or mplayer" i get a colorized pictures and broken sound qualtity.
what is the matter ?
plz help me

---

### Post by dcast on 2005-12-24
IT doesn't work with mplayer either? Is it a corrupt file? Do you have the correct plugins and codecs installed?

---

### Post by powerrangers009 on 2005-12-24
i really dont know what codes i really need for this file
i think its not a corrupt file because some people claim that they were able to play this file , but i have no idea what to do?

---

### Post by kaamos on 2005-12-24
Try this: [http://ubuntuforums.org/showthread.php?t=79449](http://ubuntuforums.org/showthread.php?t=79449)

---

### Post by kingsidy on 2005-12-24
i think that you need the necessary codecs in order to play mpg files. the packages is called  w32codecs. To install you can either search for it online or you can use a little program called Automatix. Do a search in the forums for Automatix. Using that program you can install all the codecs necessary to play mpeg files and many others.

---

### Post by GTvulse on 2005-12-24
[QUOTE=powerrangers009]hallo
i just downloaded a "mpeg"  file but im not able to play it with totem video player.
what should i do now ?
i have really no idea what should i do because when i try to play it in "totem or mplayer" i get a colorized pictures and broken sound qualtity.
what is the matter ?
plz help me[/QUOTE]

If you are using totem-gstreamer (the version in all default ubuntu installs) you will need to install the appropriate gstreamer plugin. They are quite a bunch and the best way to install them all is using the meta-packages.

In Synaptic, activate the Universe repositories and after, edit the entries to add the multiverse repositories. Search for "gstreamer0.8-plugins" and "gstreamer0.8-plugins-multiverse". That will enable Totem and Rythmbox to play almost anything.

---

