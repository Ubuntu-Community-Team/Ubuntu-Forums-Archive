---
title: "Help With Music and Videos"
date: 2006-03-08
forum: Desktop Environments
---

### Post by aairez on 2006-03-08
every time i go to play music or video, either being mp3 bassed for music or web bassed or other avi, mpg, or wma it will not play on totem, it says its missing the output, tried everyone in multimedia, still will not play, even on web bassed, also music will not play, and tested all input/output they function fine. might it be it does not work because the music is on an ntfs partiton? it will no be loaded into rythmbox. please help me out >< im so confused

---

### Post by swamytk on 2006-03-08
Follow this link: [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

---

### Post by Perfect Storm on 2006-03-08
[QUOTE=swamytk]Follow this link: [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)[/QUOTE]

Bad idea if he is using Breezy.

Instead open your terminal:

```
sudo gedit /etc/apt/sources.list

```

Uncomment the lines (the lines that have one # infront of it, simple remove the #).

also add:

[b]## Multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
[/b]

This is optional to add if you like:
[b]
## Backports
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports-staging main universe multiverse restricted

## Backports-extras
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras-staging main universe multiverse restricted

## Open Office 2 final
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

## Opera web browser
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

## Wine
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/
[/b]

then:
```
sudo apt-get update
sudo apt-get install gstreamer0.8-plugins gstreamer0.8-lame gstreamer0.8-ffmpeg w32codecs lame sox ffmpeg mjpegtools vorbis-tools libdvdcss2 gstreamer0.8-plugins-multiverse avifile-divx-plugin avifile-mad-plugin avifile-mjpeg-plugin avifile-vorbis-plugin avifile-win32-plugin avifile-xvid-plugin libdvdnav4 libdvdplay0 libdvdread3
gst-register-0.8
```


or use automatix, check my sig.

---

