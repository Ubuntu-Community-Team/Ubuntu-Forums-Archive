---
title: "kubuntu 5.10 problems"
date: 2005-09-29
forum: Desktop Environments
---

### Post by pipodnmy on 2005-09-29
i have found a few problems with kubuntu 5.10:
1) k3b setup - run as root, shows only an empty window with ok and cancel option but nothing else.
2) kaffeine crashes when i set it to use xine (using gstreamer8.0 is fine) pretty much to do anything, playing any file or DVDs. by itself xine works fine (xine-ui works fine, mplayer works fine).

---

### Post by aysiu on 2005-09-29
[https://bugzilla.ubuntu.com/](https://bugzilla.ubuntu.com/)

---

### Post by pipodnmy on 2005-09-29
well, there is always that - but i this has to work for some one so may be i am doing something wrong?! let me know if it happens for u..

---

### Post by Knome_fan on 2005-09-29
I think there are a lot of people having issues with kaffeine.
There are however some ways that seem to fix this:
1. You can install an upgraded but unofficial package from here:
[http://kudos.berlios.de/kf/kf1.html#probkaffeine](http://kudos.berlios.de/kf/kf1.html#probkaffeine)
2. Kubuntu itself also provides some updates (though they are also semi official).
Simply add ```
 deb [http://kubuntu.org/](http://kubuntu.org/) hoary-updates main 
``` to your /etc/apt/sources.list, apt-get update, apt-get upgrade and you should be ready to go.

About k3b setup not working I don't really have a clue, but have you tried starting k3b itself as root and then enter setup from there?

---

### Post by pipodnmy on 2005-10-10
yep, but same thing happens.

---

### Post by claydoh on 2005-10-10
even running "sudo k3bsetup" does not work either.

But I must ask what do you need to do which requires it to be run?  I have never had to run k3bsetup before (even in other distros) but I am sure there is another way to get what you may need done.

---

