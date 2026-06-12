---
title: "Cant install all updates - Need to uninstall other program"
date: 2006-08-03
forum: Desktop Environments
---

### Post by mister_p_1998 on 2006-08-03
I just downloaded todays updates, and they all installed apart from one - the one for Totem, it said I had to uninstall another program before it could install the update. But which one? it never said, I tried (as advised) apt-get dist-upgrade and apply updates in package manager. It still keeps saying theres an update it cant  install. 
Over to you guys.
Steve

---

### Post by philippe_carlo on 2006-08-03
Try running the update manager from the command line as follows:
```
sudo apt-get update
```

Then it should mention which packages have to be removed.

---

### Post by asplode on 2006-08-03
I checked on this a few minutes ago..
its upgrading to totem 1.4.3, and if you go into synaptic and try, you'll see why its not letting you (chances are you have totem-xine installed) whereas the dependecy for the new version is solely on totem-gstreamer, and gstreamer firefox plugin isn't even compatible with 1.4.3 yet.  I'm not going to force upgrading on it, Gstreamer just doesn't want to act right for me in totem.

---

### Post by mister_p_1998 on 2006-08-03
> **asplode said:**
> I checked on this a few minutes ago..
its upgrading to totem 1.4.3, and if you go into synaptic and try, you'll see why its not letting you (chances are you have totem-xine installed) whereas the dependecy for the new version is solely on totem-gstreamer, and gstreamer firefox plugin isn't even compatible with 1.4.3 yet.  I'm not going to force upgrading on it, Gstreamer just doesn't want to act right for me in totem.

Thanks mate,
looks like you're right, Im at work right now, so cant check my machine, but Ive got a similar install at work which DOESNT have totem-gstreamer installed, and all updates installed fine.
Thanks for the rapid response (as usual)

Steve

---

### Post by linuxguiri on 2006-09-10
you can get totem-gstreamer-firefox-plugin_1.4.3-0ubuntu1_i386.deb here:
[https://launchpad.net/distros/ubuntu/dapper/i386/totem-gstreamer-firefox-plugin/1.4.3-0ubuntu1](https://launchpad.net/distros/ubuntu/dapper/i386/totem-gstreamer-firefox-plugin/1.4.3-0ubuntu1)

---

