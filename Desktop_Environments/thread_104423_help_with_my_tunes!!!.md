---
title: "help with my tunes!!!"
date: 2005-12-16
forum: Desktop Environments
---

### Post by rjdetty on 2005-12-16
I am new to everything and i was needing to know if there is any program that plays the iTunes format for linux... all the songs are not copy protected and I am not interested in downloading stuff, I just want to be able to listen to my files... help me please???

---

### Post by localzuk on 2005-12-16
Any decent player should play the 'AAC' files produced by iTunes. Have you tried: Mplayer, xmms, vlc, totem, kaffeine?

Information about setting up codecs and music players in general is available from [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/). Codecs are available from [http://www.myplayerhq.hu/](http://www.myplayerhq.hu/).

---

### Post by kaamos on 2005-12-16
Try searchin "aac" in synaptic and read the descriptions.

---

### Post by jan-banan on 2005-12-16
i have no idea if this is nessisary, but you might have to enable a specific repository (which i dont know, i always enable alla first thing i do :P) and download w32codecs using synaptic or apt-get
i allways do this because then i can watch all video formats and listen to (almost?) every music format. 
any other package might work equally or so, but i figured you might want to watch some movies either online or from your disk.

to enable all repos write:
sudo gedit /etc/apt/sources.list 
and hit enter ;)
then you uncomment all links you see (erase the # )

maybe someone can tell which repo it is, might be usefull to know.

---

### Post by Mr. Electric Wizard on 2005-12-16
w32codecs are not in the repositories any more.
you have to get them elsewhere.

---

### Post by localzuk on 2005-12-20
Take a look at [http://ubuntuforums.org/showthread.php?t=79449](http://ubuntuforums.org/showthread.php?t=79449) to find out about the plf repo's for ubuntu.

---

