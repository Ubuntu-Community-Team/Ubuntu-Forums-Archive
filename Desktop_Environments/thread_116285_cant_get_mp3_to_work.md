---
title: "cant get mp3 to work"
date: 2006-01-12
forum: Desktop Environments
---

### Post by pillu on 2006-01-12
i cant get my mp3 or in face any other media to work on ubuntu....i looked at the wiki and then tried to install the gstreamer0.8-mad package...but it couldnt get installed...it is probably not in the repositories....i have enabled the universe and the multiverse repositories too...other programs like mplayer are not getting installed due to dependency problems...
please help me to solve the problem....
thanks

---

### Post by kaamos on 2006-01-12
Hello.

What is the contents of your /etc/apt/sources.list file?

---

### Post by lolcese on 2006-01-12
Have you tried automatix?

---

### Post by pillu on 2006-01-12
[QUOTE=kaamos]Hello.

What is the contents of your /etc/apt/sources.list file?[/QUOTE]


hi,

i have removed all the # marks from all the sources i could find in the /etc/apt/sources.list file and i changed the universe to universe multiverse...it is still not able to find the gstreamer0.8-mad in the repositories

---

### Post by kaamos on 2006-01-12
Have you ran this after changing the file
```
sudo apt-get update
```
?

If it still does not work, try generating a new list -> [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
This package takes care of most of the plugins you need: gstreamer0.8-plugins-multiverse

---

### Post by bensode on 2006-01-12
I've gotten Xmms installed with **sudo apt-get xmms** to play MP3 files that I have but still working on getting AAC (iTunes non-DRM files) to work with Xmms ...

---

### Post by kaamos on 2006-01-12
Install this:
> xmms-mp4 *- a mp4/aac audio player for xmms*

---

### Post by bensode on 2006-01-12
W00T!  Rock on!  Saves me a butload of time converting them all!  I had found Jtunes to convert them all but I have a 300+ cd library that I encoded into iTunes over the years and was dreading the amount of time to convert them all or re-rip!

---

