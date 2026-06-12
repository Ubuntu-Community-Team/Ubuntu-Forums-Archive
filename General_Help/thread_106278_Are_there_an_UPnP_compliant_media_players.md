---
title: "Are there an UPnP compliant media players?"
date: 2005-12-20
forum: General Help
---

### Post by Granduke on 2005-12-20
I'd like to try Twonkymedia which a linux version but I am unable to find a supported player for linux.  Are there any UPnP players?

---

### Post by JNik on 2006-01-13
From videolan's site

> VLC media player 0.8.4 (2005-11-2626 November 2005)  This new release features many improvements including a new VLC cone, new Mac OS X wizard and extend controls dialogs, tree playlist skins2 support, HTTP interface CGI handling, linux binary codecs loader, **UPnP** and Bonjour **service discovery**, shoutcast stream forwarding, new languages ...

---

### Post by sreyan on 2006-04-24
You can use any media player with UPnP if you have djmount installed.

unfortuneately djmount requires fuse which I've had some problems installing with out getting into group permission hell. I'll be posting a guide shortly. ps. I believe VNC is capable of UPnP.

---

### Post by sreyan on 2006-04-24
All right. You need VLC .8.4a, currently ubuntu has .8.4
 
add these to your sources.list file

deb [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sid main
deb-src [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sid main

sudo apt-get update && sudo apt-get install vlc

to enable UPnP you have to open up the playlist (ctrl+p) and there will be an option under manage>services discovery. 

I hope this Helps!

---

### Post by masterplumber on 2006-08-18
Hi,
Just installed vlc (0.8.5 from nightly build) on Dapper Drake and I don't see any service for uPnP.  I have the following Services Discovery options

Bonjour Services
SAP announcements
HAL devices detection
Shoutcast Radio Listings
Podcasts

- nothing on uPnP though.  Anyone got any ideas?  Am I missing soime kind of upnp plugin somewhere?

---

