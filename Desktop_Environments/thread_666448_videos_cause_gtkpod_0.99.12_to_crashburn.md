---
title: "videos cause gtkpod 0.99.12 to crash/burn"
date: 2008-01-13
forum: Desktop Environments
---

### Post by sledhead45 on 2008-01-13
Hi all-
I have gtkpod 0.99.12 installed from source on my feisty desktop. I also have libmp4v2-1.5.0.1 installed from source. I was wanting to get video support for my 80gb ipod classic (xB029) model A1238. Right now I get no "videos" playlist near my podcast and photos playlist. when I try to drag a known good ipod video to my ipod in gtkpod, it quits immediately and it spits out  ```
gtkpod: symbol lookup error: gtkpod: undefined symbol: MP4GetMetadataGrouping
```

when i did my gtkpod install the ./configure gave this:
```
Configuration for gtkpod 0.99.12 :
--------------------------------

 Host System Type .....: i686-pc-linux-gnu
 Install path .........: /usr/local
 GTK2 version .........: 2.10.11
 GLib2/GThread version : 2.12.11
 gnome-vfs.............: *no -- will build without iPod autodetection support
 hal...................: *no -- will build without HAL support
 libcurl ..............: *no -- will build without coverart download support
 mp4v2 ................: yes -- will build with aac support
 vorbisfile ...........: *no -- will build without ogg support
 FLAC .................: *no -- will build without FLAC support
 Preprocessor .........: gcc 
```

The ipod was initially synced with itunes on windows. Ive tryed with having a video already on this ipod via itunes and no video at all. Let me know if i'm forgetting any necessary information. thanks a bunch

--travis

---

### Post by Sikon on 2008-01-15
Generally, you shouldn't install software from source in Ubuntu, especially libraries.

You may want to try the gtkpod-aac package in this PPA: [https://launchpad.net/~sikon/+archive](https://launchpad.net/~sikon/+archive)

To do so, add this to your sources.list:

```
deb http://ppa.launchpad.net/sikon/ubuntu feisty main
```

and run:

```
sudo apt-get update
sudo apt-get install gtkpod-aac
```

Make sure to delete the version you compiled from source first.

---

### Post by eosyn on 2008-01-15
I added the deb line and updated and sure enough gtkpod-aac was updatable but it breaks with a libflac7 dependency error :( .. know how to get around that?

---

### Post by sledhead45 on 2008-01-16
sikon- your suggestion worked perfectly. Thanks for the reply.

eosyn- Have you tried going into the synaptic package manager and making sure libflac7 is installed?

--travis

---

### Post by eosyn on 2008-01-18
only libflac8 is installed. this really sucks. Why can't the maintainer just get the update out the real way instead of going through all these damn hoopsl. I'm tired of using windows to install my music.

---

