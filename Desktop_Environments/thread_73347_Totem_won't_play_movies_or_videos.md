---
title: "Totem won't play movies or videos"
date: 2005-10-08
forum: Desktop Environments
---

### Post by donkle on 2005-10-08
I'm a newbie and I need detailed instructions - please.
I can't get Totem to play movies ar anything else. I have no equipment problems. Movie and videos play fine when I use Windows XP. I have checked Help but nothing there addresses the problem. When I try to play a movie the following error message appears:
" **Totem could not play 'file:///media/cdrom1/VIDEO_TS.BUP'**.
There were no decoders found . . . . you might need to install the corresponding
plugins."

Plugins ? Decoders??

---

### Post by darkmatter on 2005-10-08
donkle. In answer to your question, Ubuntu does not carry support for proprietary formats by default (legal reasons), only open formats are supported.

If you want multimedia support for these, you must install several extra packages. You will need libdvdcss2 for DVD's, w32codecs for decoding various formats (wmv, etc), libquicktime, etc.

The easiest way to get these installed is to grab the version of Easy Ubuntu for your Ubuntu version and run the installation script.

Information/How To for EasyUbuntu can be found here: [http://ubuntuforums.org/showthread.php?t=64629](http://ubuntuforums.org/showthread.php?t=64629)

Good Luck! If you have any other questions, feel free to ask.

---

### Post by Perfect Storm on 2005-10-08
Add
> 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

To your repo.
Here's how you do. Open the terminal and write:
```

sudo gedit /etc/apt/sources.list

```
After adding the two lines, write this in the terminal:
```

sudo apt-get update
sudo apt-get install gstreamer0.8-plugins
sudo apt-get install gstreamer0.8-lame
sudo apt-get install gstreamer0.8-ffmpeg
sudo apt-get install lame
sudo apt-get install sox
sudo apt-get install ffmpeg
sudo apt-get install mjpegtools
sudo apt-get install vorbis-tools

```

Now go to this thread to install the codecs: [http://www.ubuntuforums.org/showthread.php?t=70227](http://www.ubuntuforums.org/showthread.php?t=70227)
When the codecs are installed write this in the terminal:

```
gst-register-0.8
```

You should either go for Mplayer or vlc instead of totem.
To install vlc
```

sudo apt-get install wxvlc
sudo apt-get install vlc-plugin-esd
killall gnome-panel

```

Now go to Applications ---> Sound and Video ---> VLC for GTK+

Now VLC is open, go to settings and choose preferences. In Audio check the 'Advance option' box. Now you can see an option which is call Audio driver or something similar (I'm not on my box to check it) and choose **Esound**
Save it.

---

### Post by Perfect Storm on 2005-10-08
Easy Ubuntu? Strange I havn't heard of it, I must be sleeping *lol*...gonna check what it is. :)

---

