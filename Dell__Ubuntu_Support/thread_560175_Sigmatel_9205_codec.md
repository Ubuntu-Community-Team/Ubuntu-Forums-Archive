---
title: "Sigmatel 9205 codec"
date: 2007-09-26
forum: Dell  Ubuntu Support
---

### Post by cav2200 on 2007-09-26
Having a hell of a time installing ubuntu on this dell 1500, mainly because of the intel x3100 graphics.  That's another story though.

I'm in need of a codec dump for the 9205 sigmatel that this laptop comes with for another project.  Could some kind soul post his/hers up for me?  Any help in this matter would be greatly appreciated.

---

### Post by tturrisi on 2007-09-26
You mean you can't get sound working?
[https://help.ubuntu.com/community/HdaIntelSoundHowtoh.edu/pub/suse/projects/alsa/snapshot/driver/alsa-driver-hg20070922.tar.bz2](https://help.ubuntu.com/community/HdaIntelSoundHowtoh.edu/pub/suse/projects/alsa/snapshot/driver/alsa-driver-hg20070922.tar.bz2)
note:  the guide is older and you MUST now use the latest version of alsa that should support the hda-intel Sigmatel audio & if no joy then use this version of alsa at bottom of page:
[http://www.gtlib.gatech.edu/pub/suse/projects/alsa/snapshot/driver/](http://www.gtlib.gatech.edu/pub/suse/projects/alsa/snapshot/driver/)

I have a dell d830 w/ the Sigmatel audio and I had to use the above alsa version to get my sound to work in debian sid.

---

### Post by cav2200 on 2007-09-27
No I'm trying to get sound working on a mac install on this laptop.  To do this I need a dump of the codec from a working install of linux.

Somewhere inside /proc/asound, there should be a file named codec#0, and I need someone to do a cat codec#0 > /tmp/sig9205.txt for me.  

Going to try installing Ubuntu off of a different distro, but its taking a while to download.

---

