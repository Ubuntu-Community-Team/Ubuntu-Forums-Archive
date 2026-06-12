---
title: "avi player"
date: 2009-05-08
forum: General Help
---

### Post by mikeonthebeach on 2009-05-08
what is a good avi player for ubuntu 9.04

---

### Post by taurus on 2009-05-08
There are a few but I think most people use vlc for almost all the videos/movies.  It's available from the repos.

---

### Post by Chemical Imbalance on 2009-05-08
Gnome-mplayer  (frontend for mplayer) is good.

There is also Kaffeine, XINE, Totem, etc...

Installing the ubuntu-restricted-extras package is a good idea too(includes lots of codecs).

---

### Post by jayanramesh on 2009-05-08
Dear mikeonthebeach,  	

 > vi player
what is a good avi player for ubuntu 9.04
Vlc and sm player are the good choice and it can handle almost all audio - video formates.It can be downloaded from synaptic package manager.

Thank you

---

### Post by andersonluk on 2009-06-13
> **jayanramesh said:**
> Dear mikeonthebeach,  	

 
Vlc and sm player are the good choice and it can handle almost all audio - video formates.It can be downloaded from synaptic package manager.

Thank you

Vlc and MoviePlayer only give you sound only. No video.

Any suggestion.

Thankyou.

---

### Post by synapsys on 2009-06-13
You probably need to install a package for video output e.g. xvideo.

```
sudo apt-get install libxv1
```

---

### Post by Chemical Imbalance on 2009-06-13
Also installing the package "ubuntu-restricted-extras" could help.

---

### Post by andersonluk on 2009-06-14
Thanks Synapsys and Chemical Imbalance,

After installation of yours packages,  still no video

---

### Post by MaxIBoy on 2009-06-14
VLC plays everything known to man, even if the file is corrupted.

If VLC doesn't play it, something is very, very wrong.

---

### Post by higet7 on 2009-06-14
vlc of course

---

### Post by Chemical Imbalance on 2009-06-14
> **andersonluk said:**
> Thanks Synapsys and Chemical Imbalance,

After installation of yours packages,  still no video

Do you have Compiz enabled?  Go to System, Preferences, Appearance and to the Visual Effects tab.  Try selecting "none" and see if that works.

Also, what is the file you are playing?  What extension does it have (ex. .m4a, .avi).

---

### Post by buzzmandt on 2009-06-14
try this guide:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
works for me for EVERYTHING video....

---

### Post by H2SO_four on 2009-06-14
I only use VLC player.

---

### Post by fooman on 2009-06-14
smplayer is my personal player of choice.  :)

---

### Post by ~sHyLoCk~ on 2009-06-14
> **mikeonthebeach said:**
> what is a good avi player for ubuntu 9.04

I just use the default totem movie player with all the gstreamer plugins installed, works like a charm for me.

---

### Post by fooman on 2009-06-14
they all work fine here (mplayer, smplayer, xine, totem, vlc...etc),  its the overall interface and controls that puts smplayer way out in front for me.

---

### Post by abulink@gmail.com on 2011-11-01
Hi friends, 

I'm new to ubuntu and am not very certain, 

but it seems these media file downloaded through windows dont work with Xlinx, vlc or sm players. 

for example I had down loaded a .flv file through vista which now I can not play on ubuntu players. But when I downloaded the same file through ubunto I could play it.

---

