---
title: "Logout on Video play"
date: 2016-04-13
forum: Debian
---

### Post by marouane87 on 2016-04-13
Hello :)

So, I wanted to try Debiand and I downloaded the hybrid gnome version containing non free firmware:
[http://cdimage.debian.org/cdimage/unofficial/non-free/cd-including-firmware/weekly-live-builds/amd64/iso-hybrid/](http://cdimage.debian.org/cdimage/unofficial/non-free/cd-including-firmware/weekly-live-builds/amd64/iso-hybrid/)

I wanted to start by using a live session, I was happily surprised that Wifi and mp3 worked right away. But I tried to play a video (mp4/mkv), Debian just gets out to login screen. (The problem does not occur in VM)
I have an Asus laptop with an intel graphic card.

Any one who knows how to fix this problem please?

Thank you :)

---

### Post by arochester on 2016-04-13
What player are you using?  Have you tried VLC which will play most formats out-of-the-box?

---

### Post by marouane87 on 2016-04-13
Thank you. I followed [this]("http://forums.debian.net/viewtopic.php?f=6&t=124689#p592821") . So I had no more crash, but instead an error: "Gstreamer encountered a general error"

Then I tried VLC and it worked. I don't know what's going on with Gstreamer (I installed it along with the plugins and yet the error persists in Gnome Videos). It might be related to the live session, because when searching I found a post saying that the problem disappeared after installing "Debian DVD via live USB".

Plus, I think the system is messed up now, because I tried the Stretch version, and it installed VLC and gstreamer from Jessie repositories. 

So basically, Stretch has a driver problem with my intel GPU, doesn't play videos natively without a third party tool and the repository is messed up. I think I'm going to stop this distro hoping with Debian... :)

---

### Post by arochester on 2016-04-13
The post is a bit suspect.  Installed Jessie, then used Jessie backport? 

There is a xserver-xorg-video-intel in Stretch >>> [https://packages.debian.org/stretch/xserver-xorg-video-intel](https://packages.debian.org/stretch/xserver-xorg-video-intel)

Maybe you just need sort out your sources.list for now...

---

### Post by marouane87 on 2016-04-14
Yes, couldn't understand it neither but it does work any way. 
The package xserver-xorg-video-intel is available by default in Stretch non-free, isn't it?

---

### Post by arochester on 2016-04-14
Do you wish to share your sources list (and perhaps the contents of system.list.d) with us, or have you wiped Debian out?

---

### Post by marouane87 on 2016-04-14
Thank you but I didn´t want to take "the risk" of installing before making sure everything is working, so it was a live USB session. There was no sources.list I had to create it. I can´t remember all the Content of the Folder System.list.d

---

