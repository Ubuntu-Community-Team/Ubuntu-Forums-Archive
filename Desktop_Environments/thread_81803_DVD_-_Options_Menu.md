---
title: "DVD - Options Menu"
date: 2005-10-25
forum: Desktop Environments
---

### Post by Zodiac on 2005-10-25
I use Totem-Xine to play my DVDs and don't have any problems viewing them but I am having a problem selecting options from the menu. 

I can't for the life of me seem to be able to get Subtitles to work, mostly because I never get prompted to select it. I like to watch Anime in the original Japanese with English subtitles, and I can't seem to even get to the menu on most movies. Ninja Scroll for example, just jumps right into the English dubbed movie...

How can I stop this from happening?

Thanks in advance!

---

### Post by Zodiac on 2005-10-25
:(

---

### Post by bionnaki on 2005-10-25
[QUOTE=Zodiac]

How can I stop this from happening?

[/QUOTE]

avoid totem - it sucks.
use vlc.

---

### Post by flower on 2005-10-25
you will need to add the following lines to your /etc/apt/sources.list:

     deb [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sarge main
     deb-src [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sarge main

then in console write : 

sudo apt-get update
sudo apt-get install vlc libdvdcss2

vlc - installed - enjoy

---

