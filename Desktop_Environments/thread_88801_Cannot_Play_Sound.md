---
title: "Cannot Play Sound"
date: 2005-11-11
forum: Desktop Environments
---

### Post by Efrain Valles on 2005-11-11
Hey there In Ubuntu land...

I`m a newbie and I need help installing multimedia codecs. I installed Ubuntu 5.04 a couple of months ago and I really didn't sit with it to get it sorted out. I'm barely switching from windows and I tried several threads on how to do it (Most of the URL conneting the packages are broken) and It makes it confusing. I need Mp3 playback and video play back...

Someone with a warm heart please HELP this poor new soul :???:

---

### Post by Ubuntist on 2005-11-11
[Please ignore]

---

### Post by Hairy_Palms on 2005-11-11
you can install it by entering these commands

sudo apt-get install gstreamer0.8-plugins
sudo apt-get install gstreamer0.8-lame
sudo apt-get install gstreamer0.8-ffmpeg
sudo apt-get install lame
sudo apt-get install sox
sudo apt-get install ffmpeg
sudo apt-get install mjpegtools
sudo apt-get install vorbis-tools
gst-register-0.8

to paly back .wma and .wmv quicktime, etc then download the codecs from
[http://www2.mplayerhq.hu/MPlayer/rel...050412.tar.bz2](http://www2.mplayerhq.hu/MPlayer/rel...050412.tar.bz2)
then extract them to the folder **/usr/lib/win32**

---

