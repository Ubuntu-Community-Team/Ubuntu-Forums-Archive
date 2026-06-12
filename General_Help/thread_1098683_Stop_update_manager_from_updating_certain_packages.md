---
title: "Stop update manager from updating certain packages?"
date: 2009-03-17
forum: General Help
---

### Post by phr0ze on 2009-03-17
I installed Blueman bluetooth manager by adding the PPA repo. This package either removed or downgraded the bluez packages. However update manager keeps asking me to update these packages. 

Everything in blueman is working perfectly. I want to stop being harassed by the update manager for these packages. Can I tell apt to ignore these by name?

Thanks,
John

---

### Post by buldozerceto on 2009-03-17
I really hate the update manager, how to completely remove it?

---

### Post by ruel- on 2009-03-17
```
sudo aptitude hold pkgname
```

hope it helps..

---

### Post by phr0ze on 2009-03-18
Thanks, That looks like the solution. However I wanted to read more about it and ended up finding a better solution. I don't like mixing aptitude with apt-get, I'm never sure of which is going to behave right. I wish apt-get had the hold option.

Anyways here is the APT-GET solution (from [http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html))

Just need to edit/create the file /etc/apt/preferences. 

added these lines

     Package: bluetooth
     Pin: version 4.12-0ubuntu5
     Pin-Priority: 1001

     Package: bluez-alsa
     Pin: version 4.12-0ubuntu5
     Pin-Priority: 1001

     Package: bluez-cups
     Pin: version 4.12-0ubuntu5
     Pin-Priority: 1001

     Package: bluez-gstreamer
     Pin: version 4.12-0ubuntu5
     Pin-Priority: 1001

     Package: bluez-utils
     Pin: version 4.12-0ubuntu5
     Pin-Priority: 1001

If I ever want to upgrade them again, I can just clean this out of the preferences file.

---

### Post by drs305 on 2009-03-18
I have found that even with a hold placed with apt, gui updates via update manager and synaptic can still attempt to upgrade the package. You can prevent this by locking the version in synaptic. (Highlight, then Package, Lock Version)

---

