---
title: "NOICE in the sound"
date: 2005-05-17
forum: Desktop Environments
---

### Post by Peter84 on 2005-05-17
Hi i just started using ubuntu, and i love it!! BUT i have a problem with the sound. 
Theres a noice i the sound picture! When i play music (mp3) it is like they are singing in a can!! I think the problem startet when i used the "How to configure sound to work properly in GNOME?" place in the ubuntuguide.org
Plz help!!

---

### Post by harryc on 2005-05-17
The "How to configure sound to work properly in GNOME" had you backup your old esd.conf file. Replace that with the original. If that doesn't work,  reverse what the howto said to do. In looking at it quickly, it appears that you need to restore a backed up esd.conf, delete a newly created asound.conf. remove a package - libesd-alsa0, and delete a symlink.

[http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)

---

### Post by fng on 2005-05-17
Using alsa, my gaim sounds are also noisy.  If i remember correct, the same noisy sounds occured with esd.

The funny thing is, it's only noticable with gaim.  All the other sounds are perfect,

---

