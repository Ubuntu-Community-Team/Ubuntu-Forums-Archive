---
title: "Movie player"
date: 2005-12-14
forum: General Help
---

### Post by Loggy on 2005-12-14
Can anyone recommend a good movie player that will play a DVD when inserted into my Kubuntu laptop (Dell Inspiron 6000)?

I tried Mplayer from it's own site but hit a codec problem.  And kaffeine didn't work on the first DVD I tried.:( 

Is there a Kubuntu build of Mplayer or something similar available?  I can't see anything in Synaptic.

TIA

---

### Post by Zelut on 2005-12-14
I don't use KDE but under gnome xine works like a charm for all of my movies.  Might want to take a look at that.. I got the instructions from the [www.ubuntuguide.org](www.ubuntuguide.org) (for installation & codecs you'll need)

---

### Post by lutrafobic on 2005-12-14
Take a look at "Videolan" (aka VLC)

[http://www.videolan.org/vlc](http://www.videolan.org/vlc)

(use the 'debian' installation method)

---

### Post by DoeRayMe on 2005-12-14
> sudo apt-get install kaffeine-xine

the above is found in the universe repoisitry, make sure you un-comment it from your sources.list ;)

Make sure you have libdvdcss2 installed from the PLF repo, if you have'nt got that installed, add this to your sources.list

> deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

then 

> sudo apt-get update

then

> sudo apt-get install libdvdcss2

also the w32codecs can also be installed from that repo, if needed that is

> sudo apt-get install w32codecs

---

### Post by localzuk on 2005-12-14
The problem you are having is probably not due to the software itself, more due to lack of support for playing DVD's in ubuntu as standard. Try the instructions at [http://www.ubuntuguide.org/#dvdplayback](http://www.ubuntuguide.org/#dvdplayback) (also, follow the instructions at [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories) beforehand - note that the instructions are for 'Hoary 5.04' and not 'Breezy 5.10' - so references to 'hoary' should be changed to 'breezy' where applicable.

---

