---
title: "No sound in mpg"
date: 2006-09-01
forum: Desktop Environments
---

### Post by JNowka on 2006-09-01
Ok I have installed the W32codecs, mpg123, libmpeg3-1, libmpeg2-4, libsmpeg0, libmad0, gstreamer0.10-ffmpeg.  And yet I am unable to watch .mpg files in totem-xine.  

I have tried the mpeg plug in for XMMS it has sound, but choppy as hell. 

I knew that the gstreamer plugin was mostly a long shot and was guessing that it wouldn't work because I am running totem-xine.  

I don't look forward to downloading VLC or VCL or whatever over dialup so can anyone help me out when it comes to getting mpg files to work under totem or xmms.  I have played around with settings until I am blue in the face.

Thanks for your help

---

### Post by taurus on 2006-09-01
I've never liked the totem thing and I always use mplayer to handle all my movies.  It plays everything that I throw at it, including avi, mpg, bin, iso, img, etc.

---

### Post by JNowka on 2006-09-01
when I click on mplayer in my menu it opens up totem.  is there a differant mplayer?

---

### Post by taurus on 2006-09-01
You have to install mplayer with apt-get/aptitude/synaptic...  You can check to see if you have mplayer on your system with (from a terminal:  Applications -> Accessories -> Terminal)

```
whereis mplayer
```

---

### Post by JNowka on 2006-09-01
all I get is "mplayer:"

---

### Post by taurus on 2006-09-01
It means that you don't have mplayer on your machine.  It doesn't come as a default so you have to install it with apt-get/aptitude/synaptic.  However, you need to remove the # sign in front of all the lines in /etc/apt/sources.list with universe & multiverse at the end...

```
gksudo gedit /etc/apt/sources.list
```
Save it and then run

```

sudo aptitude update
sudo aptitude install mplayer

```
Or you can use synaptic and at the Search field, type in "mplayer" to search for it.

---

### Post by JNowka on 2006-09-01
Ok I am downloading it now.  Saddly I don't have the internet running on my Linux box so I have to download it using my Windows computer onto a network drive that is located on the ubuntu machine.  I know its the long way around but it serves my purpose.

---

### Post by JNowka on 2006-09-01
Ok, now this is awsome.  Thank you for the heads up. :D

---

