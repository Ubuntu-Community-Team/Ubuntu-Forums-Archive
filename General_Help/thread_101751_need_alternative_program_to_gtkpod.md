---
title: "need alternative program to gtkpod"
date: 2005-12-10
forum: General Help
---

### Post by MikeMay on 2005-12-10
I am looking for an alternative program to gtkpod. With gtkpod
I cant use my aac (m4a) files cause it cant handle them. I tried
to compile it with aac support but it doesnt work.

Are there any other programs that can be used ti sync my music 
with an iPod? They should be able to handle mp3 and m4a.

Thanks!

---

### Post by ren wins on 2005-12-10
did you try installing the multimedia codecs for nonfree media?
```
sudo apt-get install gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-ffmpeg 
```

[https://wiki.ubuntu.com/RestrictedFormats#head-98f0945855102afe97a542ae07168f3ddcc61124](https://wiki.ubuntu.com/RestrictedFormats#head-98f0945855102afe97a542ae07168f3ddcc61124)
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-music-and-movies](http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-music-and-movies)

hope this helps

---

### Post by MikeMay on 2005-12-10
> did you try installing the multimedia codecs for nonfree media?

No ... but GTKPod needs to be compiled with AAc support.
Does your GTKPod work with AAC?
The GTKPod from Ubuntu isnt compiled with that option.
To compile it you need mpeg4ip ... that package is not
part of Ubuntu and conflicts with libmp4v2.

---

### Post by WanderingStar on 2005-12-10
I was having the same problem - so I turned to Amarok.  Specifically compiled from SVN as per the instructions [here: ]("http://www.ubuntuforums.org/showthread.php?t=80492&highlight=amarok").  Part of the script allows you to pass options to the configure process.  You need to add "--with-mp4v2 --with-libgpod" (minus the quotes) in the dialogue box.  You will need the package libmp4v2-2 dev installed.  You also need to compile and install libgpod from [Here]("http://www.gtkpod.org/libgpod.html").  Its pretty simple to install (./configure, make, sudo make install).  I'm not sure what packages it needs specifically - I have the dev packages for pretty much everything installed. At very least you will need build-essential. If you get errors, post them here and we can figure it out.

---

