---
title: "Media issues"
date: 2006-02-19
forum: Desktop Environments
---

### Post by Phaeton on 2006-02-19
I just made the switch from Windows XP Pro to the latest version of Ubuntu after backing up all my media (music, video, etc.) onto an external HD.

The external HD works fine, and displays all the files.

My issue regards Rhythmbox and Totem. For some reason or another, Rhythmbox wont play my MP3s and Totem can't play any of my video, even my Mpegs; however, Rhythmbox has no trouble with playing WAV files from the aforementioned drive. The error message the program gives is (to me, anyway) entirely bogus: "the file is not an audio stream" followed by the path and file name.

PLEASE HELP ME. I escaped the clutches of Windows so I could listen to my music in peace.

---

### Post by Perfect Storm on 2006-02-19
Firstly you need to enable universe and multiver in your sourcelist to get access to the whole repo. + getting PLF.

```
sudo gedit /etc/apt/sources.list

```

Uncomment the lines where there's only one **#**

also add:

[b]## Multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
[/b]

optional to add:

[b]## Backports
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports-staging main universe multiverse restricted

#backports-extras
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras-staging main universe multiverse restricted

# Open Office 2 final
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

# Opera web browser
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

## Wine
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/
[/b]

Now

```
sudo apt-get update
sudo apt-get install gstreamer0.8-plugins gstreamer0.8-lame gstreamer0.8-ffmpeg w32codecs lame sox ffmpeg mjpegtools vorbis-tools libdvdcss2 gstreamer0.8-plugins-multiverse avifile-divx-plugin avifile-mad-plugin avifile-mjpeg-plugin avifile-vorbis-plugin avifile-win32-plugin avifile-xvid-plugin libdvdnav4 libdvdplay0 libdvdread3
gst-register-0.8
```

But my recommendation is for movie/media player: mplayer and/or VLC
Mp3/ogg/music player: xmms or bmp

---

