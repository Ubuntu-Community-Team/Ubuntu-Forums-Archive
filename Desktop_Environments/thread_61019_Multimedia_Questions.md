---
title: "Multimedia Questions"
date: 2005-08-30
forum: Desktop Environments
---

### Post by BluBoy on 2005-08-30
Hey, just have two very quick questions...

1) I would like to backup some DVDs - When I attempt to apt-get dvdrip, it fails on dependencies (Wants transcode, which wants libavifile-0.7 which fails despite being the latest version)
Any ideas?

2) What is a decent media player?  I'm happy to continue to use XMMS for MP3/OGGs but I want a decent Video player that supports atleast AVI, MPEG, DIVX, ASF, WMV, DVD.  
I have MPlayer installed at the moment, but I dont like the seperate control panel (And also the fact that when I select all my videos, it tries to open them individually... Creating a play list is just a pain in the arse)
Totem just does not seem to work regardless, it says no decoders found (w32codecs IS installed)
How can I fix Totem... Or what other media players do you guys recommend?

(I am running Breezy packages with a few extra apt rep's...  But it doesn't seem to be a Breezy problem, which is why I posted here)

Thanks!

--
BluBoy

---

### Post by Lord Illidan on 2005-08-30
> 2) What is a decent media player? I'm happy to continue to use XMMS for MP3/OGGs but I want a decent Video player that supports atleast AVI, MPEG, DIVX, ASF, WMV, DVD. 

Xine is excellent. As far as I know it can play all those above, though I am not so sure about DIVX, ASF and WMV. It excels in DVD playing however.

> 1) I would like to backup some DVDs - When I attempt to apt-get dvdrip, it fails on dependencies (Wants transcode, which wants libavifile-0.7 which fails despite being the latest version) 

Try using synaptic to force libavifile to a lower version which transcode accepts. Also using breezy packages can confound your system somewhat..

---

### Post by BluBoy on 2005-08-30
[QUOTE=Lord Illidan]Try using synaptic to force libavifile to a lower version which transcode accepts. Also using breezy packages can confound your system somewhat..[/QUOTE]
No go with this.

```
transcode:
 Depends: libavifile-0.7c102 (>=1:0.7.43.20050224-1) but it is not installable

``` 

BUT - I have libavifile-0.7 version 1:0.7.43.20050224-1ubuntu6 installed (Which by my reckoning, should meed the requirments)

[QUOTE=Lord Illidan]Xine is excellent. As far as I know it can play all those above, though I am not so sure about DIVX, ASF and WMV. It excels in DVD playing however.[/QUOTE]
Is there a way to uninstall Totem?

Cheers!

---

