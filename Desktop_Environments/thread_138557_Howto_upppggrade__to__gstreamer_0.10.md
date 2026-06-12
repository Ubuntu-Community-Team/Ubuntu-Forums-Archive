---
title: "Howto upppggrade  to  gstreamer 0.10?"
date: 2006-03-02
forum: Desktop Environments
---

### Post by JohnnyWalker on 2006-03-02
I have problems getting windows media player formats to work in ubuntu.

I understand that gstreamer is the standard media framework in Linux/Unix and that the latest version of Ubuntu uses an old version of gstreamer (0.8), and that automatic upgrade to latest version of gstreamer is not possible througt the package update tools provided as standard.

How do I upgrade to gstreamer 0.10, the easiest way?

---

### Post by Ramses de Norre on 2006-03-02
Search for the .deb package or the source on internet.

---

### Post by kaamos on 2006-03-02
Easiest way? Upgrade your ubuntu to dapper. The apps in breezy are designed for 0.8 and will most likely not work with 0.10. But you really should not do this because you are having trouble playing some files.. What problems do you have exactly?

---

### Post by JohnnyWalker on 2006-03-02
I cannot play the videos at [www.dr.dk/grandprix](www.dr.dk/grandprix), tried a lot of mplayer package variants.

---

### Post by speedsix on 2006-03-02
There is a gstreamer plugin that wraps the win32 binary codecs called pitfdll. Install via synaptic.

---

### Post by JohnnyWalker on 2006-03-20
vmware@vmware-bavm:~$ sudo apt-get install pitfdll
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package pitfdll

Could not find it in synaptic either, but that is the same repository, is'nt it? I have enabled all repositories, multiverse and universe.

---

### Post by Sutekh on 2006-03-20
```
sudo apt-get install gstreamer0.8-pitfdll
```

---

### Post by JohnnyWalker on 2006-03-22
Great! that works,  to some extent anyway. I can now click a video in firefox and view it.

There is however still a problem, when clicking the link "Se vindersangen, 'Twist Of Love'", this is not the one opening,  but another one on the same page.

I assume someone is  interested in hearing this. Where shall a report be sent?

BTW, what exactly was needed from a standard Ubuntu 5.10 system, I have installed and reinstalled so much so that I  dont know what made the trick, and want to write down the instructions for someone, will it do with only:

sudo apt-get install w32codecs
sudo apt-get install gstreamer0.8-pitfdll

---

### Post by missmoondog on 2006-03-22
first time i've heard of the pitfdll, but that's not saying much either!
anyway, every link on that page you reference works for me. in totem even!
i have occassional problems here and there, but can live with it for now. am going to mark this thread for future refernce.

---

### Post by pvossen on 2006-06-07
Hey, thanks. I had accidentally lost my my pitfdll file. I wanted to reinstall.
However, somehow Synaptic permanently removed it. I tried to refresh the
repository, but that didn't take. So thankfully for your link it looks like I
have it available.

---

