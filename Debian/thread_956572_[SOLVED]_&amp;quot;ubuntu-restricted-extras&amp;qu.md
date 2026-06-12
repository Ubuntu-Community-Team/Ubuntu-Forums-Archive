---
title: "[SOLVED] &amp;quot;ubuntu-restricted-extras&amp;quot; for Debian?"
date: 2008-10-23
forum: Debian
---

### Post by Lowcountry on 2008-10-23
I'm installing Debian Stable on an old Dell Optiplex, that I plan to use to mostly play music from Rhythmbox.  I use "ubuntu-restricted-extras" on my Ubuntu machine, and was curious if there were an easy way to do that with Debian.
Would this work?
```
sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui
```

EDIT:
This may work better?
```
sudo apt-get intall flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libdvdread3 liblame0 msttcorefonts sun-java6-jre sun-java6-plugin unrar
```

---

### Post by basenvironment on 2008-10-23
if you need them then I guess that works....what are you playing

---

### Post by kerry_s on 2008-10-23
in debian use multimedia:
[http://debian-multimedia.org/](http://debian-multimedia.org/)

add to your /etc/apt/sources.list:
```
deb http://www.debian-multimedia.org etch main
```

su
_apt-get update_

for the key:
```
wget http://debian-multimedia.org/gpgkey.pub -O - | apt-key add - && apt-get install debian-multimedia-keyring 
```

also don't forget to turn on contrib and non-free.

---

