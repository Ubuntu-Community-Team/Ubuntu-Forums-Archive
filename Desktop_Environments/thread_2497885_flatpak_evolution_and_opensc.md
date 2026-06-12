---
title: "flatpak evolution and opensc"
date: 2024-05-21
forum: Desktop Environments
---

### Post by chubbypiper on 2024-05-21
I have been trying to figure out how to use the current version of Evolution (3.52) on 22.04 so I can get access to M365/Graph API instead of EWS.  Unfortunately the current version for 22.04 (3.44) doesn't support it.  I figured I would try the flatpak version.  One requirement I do have is the ability to do S/MIME signing and encryption via OpenSC.  I have that oworking successfully in the non-flatpak version, but it doesn't want to work in the flatpak version.  I did a bunch of searching around, and it seem that OpenSC functionality instead of flatfak has been dubious at best.  One thing that I kept coming across was that the best bet to get it to work was to build the flatpak yourself.

So, I followed the instructions at [https://gitlab.gnome.org/GNOME/evolution/-/wikis/Evolution%20in%20Flatpak](https://gitlab.gnome.org/GNOME/evolution/-/wikis/Evolution%20in%20Flatpak) and built the stable version.  However, even though --socket=pcsc is defined as a flag in the json and I was originally thinking that would pull in OpenSC, I'm starting to think that's just defining what flags it would accept when invoked with `flatpak run org.gnome.Evolution`.  I'm not very knowledgeable with the intricate details of how flatpaks work, especially when it comes to building them.   

When pcsc stuff still wasn't working, even in the locally built flatpak, I did a `flatpak enter org.gnome.Evolution /bin/bash` and discovered that none of the normal tools or libraries I would expect were there (eg. /usr/bin/pcsc_scan or /usr/lib/x86_64-linux-gnu/opensc-pkcs11.so). 

Sorry for the rambling, but I thought some background might help as I ask, does anyone know of any documentation I could go over, or just know how, that I could use use to figure out how to build the flatpak so that it includes the OpenSC tools and libraries?

---

