---
title: "Realplayer10gold"
date: 2005-12-26
forum: General Help
---

### Post by ironwoodcarver on 2005-12-26
I wonder if there are any plans to include RealPlayer10gold in the futre as a complete package rather then having to go and confert rpms which i find a hassle the reason I ask this is that over the last couple of days I have been trying to get the Trans-siberian orgestra site to run their vidio on my machine and it will play on realplayer but not totem which I have nothing but probs with. Try logging on to their site and you will see a list of players they support and totem is not one of them but realplayer is their video is great have seen it on a windows machine but not linux all though Redhat does have it avialable but I consider Fedora more limiting in other areas and prefer Ubuntu so please I'm no programer and would not know how to make a package I hope some one else can.
Thanks and all the best to all in this hiliday season

---

### Post by anil_robo on 2005-12-26
Realplayer is an important multimedia player these days, especially with streaming music, and it must be included (and installed) with Ubuntu by default. Even mp3 codecs etc. should be installed by default, but I've been reading about "copyright" issues and things like that.

---

### Post by ironwoodcarver on 2005-12-26
I love Amarok but for video I would love to use Realplayer and as far as copyrights if fedora can get why can't Ubuntu? :confused:

---

### Post by jtbl on 2005-12-26
RealPlayer 8 is already in the 5.10 repositories and so is HelixPlayer 1.0.6, which is what RealPlayer 10 for Linux is based on.  RealPlayer 10 should be easy to backport because it already contains almost everyting it needs.  The only thing thats needed is libstdc++ for gcc 3.3 which is already in the repositories.  Fedora doesnt't use RealPlayer they use HelixPlayer which is exactly like RealPlayer but without any "non-free" codecs.

---

### Post by &#1055;&#1054;&#1055;&#1058;&#1054;&#1053;&#1046; on 2005-12-26
Go [here](http://www.mplayerhq.hu/homepage/design7/dload.html) and download the "all" codec package, uncompress it, then copy the entire directory of files from that package to /usr/lib/win32 (you will have to use "sudo" for this and make the directory as it doesn't exist by default). 

Go to synaptic and install totem-xine and xine-ui (xine-ui just because, even if you don't like using it, the UI makes it easy to configure). Open xine, settings, and on the first panel choose level as "master of known universe." Restart xine and go to the "decoder" tab of "settings" and make sure both path entries are set to /usr/lib/win32. 

You should then be able to "point and click' every video at that site (I just tried it and it works perfectly, though I'm on dialup so it doesn't... but it should work for you)

---

### Post by F for Fragging on 2005-12-26
Read these instructions to get a .deb of Realplayer 10:

[https://wiki.ubuntu.com/RestrictedFormats#head-848295cba1b3591a4b4a0dbea5844fd5d2894b6b](https://wiki.ubuntu.com/RestrictedFormats#head-848295cba1b3591a4b4a0dbea5844fd5d2894b6b)

It's downloadable here: [ftp://ftp.nerim.net/debian-marillat/pool/main/r/realplay/realplayer_10.0.6-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/main/r/realplay/realplayer_10.0.6-0.0_i386.deb)

---

### Post by ironwoodcarver on 2005-12-26
Thanks to all

---

