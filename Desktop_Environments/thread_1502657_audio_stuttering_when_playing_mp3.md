---
title: "audio stuttering when playing mp3"
date: 2010-06-05
forum: Desktop Environments
---

### Post by chrone on 2010-06-05
ubuntu lucid 10.04 with the latest update up to june 6, 2010, could not play mp3 files smoothly. it always stutter randomly.

i'm using gigabyte amd 780g chipset with realtek high definition audio chipset.

how to fix this issue?

---

### Post by hojjan on 2010-06-06
This is an issue with pulse audio that affects multimedia. There's no proper fix as far as I know. 

I also have a 780G motherboard, and I experienced the same thing. I ended up simply replacing pulse with alsa, and now my multimedia plays stutter free. Not optimal, but it works as intended.

```
sudo apt-get purge libcanberra-pulse pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-udev   pulseaudio-module-x11 gstreamer0.10-pulseaudio pulseaudio-utils pavucontrol 

sudo apt-get install gnome-alsamixer alsa-oss python-alsaaudio
```

Check out this PPA if you want to restore some functionality like media key volume control etcetera:

[https://launchpad.net/~dtl131/+archive/ppa/](https://launchpad.net/~dtl131/+archive/ppa/)

EDIT: Here are some links:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/569814/](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/569814/)
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/572580](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/572580)
[http://ubuntuforums.org/showthread.php?t=1471262](http://ubuntuforums.org/showthread.php?t=1471262)

---

### Post by MedianMajik on 2010-06-06
Do a forum search for sound problems as we have a fantastic, comprehensive thread on just that.  Clearly the problems lies in not having properly configured your sound (yet).

---

### Post by chrone on 2010-06-06
> **hojjan said:**
> This is an issue with pulse audio that affects multimedia. There's no proper fix as far as I know. 

I also have a 780G motherboard, and I experienced the same thing. I ended up simply replacing pulse with alsa, and now my multimedia plays stutter free. Not optimal, but it works as intended.

```
sudo apt-get purge libcanberra-pulse pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-udev   pulseaudio-module-x11 gstreamer0.10-pulseaudio pulseaudio-utils pavucontrol 

sudo apt-get install gnome-alsamixer alsa-oss python-alsaaudio
```

Check out this PPA if you want to restore some functionality like media key volume control etcetera:

[https://launchpad.net/~dtl131/+archive/ppa/](https://launchpad.net/~dtl131/+archive/ppa/)

EDIT: Here are some links:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/569814/](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/569814/)
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/572580](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/572580)
[http://ubuntuforums.org/showthread.php?t=1471262](http://ubuntuforums.org/showthread.php?t=1471262)

thanks for the info, i'll give it a try tomorrow at the office. :)

---

